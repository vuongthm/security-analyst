---
id: soc-notes:introduction-to-siem
translationKey: soc-notes:introduction-to-siem
slug: introduction-to-siem
title: "SIEM: đọc log đăng nhập Windows và kiểm chứng cảnh báo"
description: "Phân biệt sự kiện Windows 4624, 4625; truy vấn log trong Microsoft Sentinel và kiểm chứng giả thuyết trước khi phân loại sự cố."
date: 2026-11-10
status: published
outline: true
module: core-soc-solutions
order: 2
topics: [soc, security]
tags: [soc, blue-team]
kind: writeup
level: intermediate
lock: false
---

## SIEM giải quyết việc gì?

Một [SIEM](glossary:siem "Security Information and Event Management: hệ thống tập trung và phân tích dữ liệu sự kiện phục vụ giám sát an ninh.") giúp tập hợp dữ liệu, tìm kiếm hoạt động đáng chú ý và hỗ trợ điều tra. Nó cần nguồn log phù hợp, quy tắc phát hiện và người phân tích; có một dashboard không đồng nghĩa đã giám sát đầy đủ.

Bài này dùng sự kiện xác thực Windows để đi từ quan sát đến câu hỏi điều tra, thay vì gán nhãn tấn công chỉ từ vài lần nhập sai mật khẩu.

## Đọc đúng sự kiện đăng nhập Windows

| Event ID | Ý nghĩa | Điểm cần chú ý |
| --- | --- | --- |
| `4624` | Một phiên đăng nhập được tạo thành công | Ghi nhận trên máy đích, nơi phiên được tạo |
| `4625` | Một lần đăng nhập thất bại | Xem thêm loại đăng nhập, tài khoản và mã lỗi |

Những ID này thuộc **Microsoft-Windows-Security-Auditing**. Cần kiểm tra chính sách audit và việc thu thập log trước khi dựa vào sự hiện diện hoặc vắng mặt của chúng.

Không phải lần đăng nhập nào cũng có IP nguồn hữu ích. Trường mạng có thể trống hoặc không áp dụng, tùy loại đăng nhập và ngữ cảnh xác thực. `LogonType`, tài khoản đích, máy phát sinh và `Status`/`SubStatus` của lỗi giúp đọc sự kiện chính xác hơn.

## Truy vấn trong Microsoft Sentinel

Khi log Windows được thu thập vào bảng `SecurityEvent`, có thể dùng KQL sau để tìm nhóm có cả đăng nhập thất bại và thành công trong cùng một cửa sổ năm phút:

```kusto
SecurityEvent
| where TimeGenerated >= ago(24h)
| where EventID in (4624, 4625)
| where isnotempty(IpAddress) and IpAddress != "-"
| where isnotempty(TargetAccount) and TargetAccount != "-"
| summarize
    Failed = countif(EventID == 4625),
    Succeeded = countif(EventID == 4624)
  by Computer, TargetAccount, LogonType, IpAddress, bin(TimeGenerated, 5m)
| where Failed >= 5 and Succeeded >= 1
| order by TimeGenerated desc
```

Truy vấn yêu cầu workspace có bảng và các cột trên. Ngưỡng năm lần thất bại là lựa chọn để phân tích, cần điều chỉnh theo môi trường. Cửa sổ `bin(..., 5m)` là các khoảng cố định, không phải cửa sổ trượt.

Kết quả **không chứng minh thất bại xảy ra trước thành công**. Nó chỉ cho biết hai loại sự kiện cùng xuất hiện trong một nhóm thời gian. Muốn xác định thứ tự, mở các bản ghi gốc của nhóm đó và sắp xếp theo `TimeGenerated`.

## Từ kết quả đến giả thuyết

Một chuỗi thất bại và thành công có thể liên quan tới nhập sai mật khẩu, cấu hình dịch vụ cũ hoặc thử thông tin xác thực. Chỉ số đếm chưa đủ xác nhận brute force hay chiếm tài khoản.

Các bước đối chiếu cần thiết:

1. Kiểm tra tài khoản, máy và loại đăng nhập có thuộc cùng hoạt động không.
2. Xem mã lỗi, lịch đổi mật khẩu, tác vụ dịch vụ và lịch sử truy cập của tài khoản.
3. Đối chiếu MFA và log của hệ thống danh tính tương ứng, nếu có.
4. Tìm tiến trình, thay đổi quyền hoặc truy cập dữ liệu sau phiên thành công.
5. Kiểm tra log trùng, chậm thu thập, chênh lệch đồng hồ và trường dữ liệu thiếu.

IP nguồn có thể là proxy, NAT hoặc một điểm ra dùng chung. Nó không phải định danh chắc chắn của một người.

## Ghi nhận kết luận

Kết luận cần nêu rõ quan sát, bằng chứng đã đối chiếu, tác động và việc cần làm tiếp theo. Khi bằng chứng chưa đủ, giữ giả thuyết mở và chuyển tiếp theo quy trình SOC của đơn vị.

SIEM giúp thu hẹp phạm vi điều tra. Quyết định phân loại sự cố vẫn cần bối cảnh và tiêu chí xử lý rõ ràng.

## Tài liệu đối chiếu

- [Microsoft Learn: tổng quan Microsoft Sentinel SIEM](https://learn.microsoft.com/en-us/azure/sentinel/overview).
- [Microsoft Learn: sự kiện 4624](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4624).
- [Microsoft Learn: sự kiện 4625](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4625).
- [Microsoft Learn: cấu trúc bảng SecurityEvent](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/securityevent).
- [NIST SP 800-61 Rev. 3: ứng phó sự cố](https://csrc.nist.gov/pubs/sp/800/61/r3/final).

```quiz
{
  "title": "Tự kiểm tra: đọc log với SIEM",
  "questions": [
    {
      "id": "siem-role",
      "question": "Theo bài, điều gì cần có để SIEM hỗ trợ giám sát có ý nghĩa?",
      "options": [
        "Chỉ cần có một dashboard nhiều biểu đồ.",
        "Chỉ cần thu thập thật nhiều log, không cần xem nội dung.",
        "Chỉ cần bật mọi quy tắc với cùng một ngưỡng cố định.",
        "Nguồn log phù hợp, quy tắc phát hiện và người phân tích."
      ],
      "answer": 3,
      "explanation": "SIEM hỗ trợ tập hợp, tìm kiếm và phân tích dữ liệu. Hiệu quả giám sát còn phụ thuộc dữ liệu, logic phát hiện và hoạt động kiểm chứng."
    },
    {
      "id": "windows-4624",
      "question": "Sự kiện Windows 4624 trong phạm vi Microsoft-Windows-Security-Auditing mô tả điều gì?",
      "options": [
        "Một phiên đăng nhập được tạo thành công trên máy đích.",
        "Một lần đăng nhập thất bại với mọi loại mã lỗi.",
        "Việc bật chính sách audit trên máy.",
        "Một tài khoản chắc chắn bị kẻ tấn công chiếm."
      ],
      "answer": 0,
      "explanation": "4624 ghi nhận việc tạo phiên đăng nhập thành công tại máy được truy cập. Việc đăng nhập thành công tự nó không xác định phiên đó hợp lệ hay độc hại."
    },
    {
      "id": "windows-4625",
      "question": "Khi đọc Windows Event ID 4625, cần hiểu đây là loại sự kiện nào?",
      "options": [
        "Một phiên đăng nhập thành công đã được xác minh an toàn.",
        "Một phát hiện brute force đã được xác nhận tự động.",
        "Một lần đăng nhập thất bại; cần đọc thêm ngữ cảnh và mã lỗi.",
        "Một lần xác thực MFA đã thành công."
      ],
      "answer": 2,
      "explanation": "4625 liên quan tới đăng nhập thất bại. Loại đăng nhập, tài khoản và Status/SubStatus giúp phân tích, thay vì suy ra ngay một cuộc tấn công."
    },
    {
      "id": "fixed-bins",
      "question": "Trong truy vấn của bài, bin(TimeGenerated, 5m) tạo cách nhóm thời gian nào?",
      "options": [
        "Một cửa sổ trượt riêng bắt đầu tại từng sự kiện.",
        "Các khoảng thời gian cố định có kích thước năm phút.",
        "Một khoảng duy nhất gồm toàn bộ lịch sử của workspace.",
        "Một nhóm được sắp thứ tự chính xác từng lần đăng nhập."
      ],
      "answer": 1,
      "explanation": "bin làm tròn thời gian xuống ranh giới của khoảng có kích thước đã chọn. Nó không tự tạo cửa sổ trượt hoặc giữ thứ tự của mọi bản ghi gốc."
    },
    {
      "id": "counts-not-sequence",
      "question": "Một dòng kết quả có Failed = 5 và Succeeded = 1. Kết luận nào được truy vấn này hỗ trợ?",
      "options": [
        "Năm lần thất bại chắc chắn diễn ra trước lần thành công.",
        "Tài khoản đã bị chiếm vì một lần đăng nhập thành công xuất hiện.",
        "Có cả hai loại sự kiện trong cùng nhóm; chưa chứng minh lần thất bại xảy ra trước lần thành công.",
        "Hai loại sự kiện chắc chắn đến từ hai máy khác nhau."
      ],
      "answer": 2,
      "explanation": "summarize đếm sự kiện theo nhóm. Để kiểm tra trình tự, cần mở các bản ghi gốc tương ứng và xem thứ tự TimeGenerated."
    },
    {
      "id": "detection-threshold",
      "question": "Ngưỡng Failed >= 5 trong bài nên được hiểu thế nào?",
      "options": [
        "Một lựa chọn phân tích cần điều chỉnh theo môi trường và kiểm chứng bằng ngữ cảnh.",
        "Ngưỡng bắt buộc chứng minh brute force trong mọi tổ chức.",
        "Điều kiện bảo đảm không thể có cảnh báo sai.",
        "Điều kiện làm cho việc kiểm tra tài khoản và mã lỗi trở nên không cần thiết."
      ],
      "answer": 0,
      "explanation": "Ngưỡng đếm chỉ giúp chọn nhóm cần chú ý. Thói quen sử dụng, dịch vụ, dữ liệu và quy trình của môi trường có thể đòi hỏi cách đánh giá khác."
    },
    {
      "id": "audit-and-collection",
      "question": "Không thấy sự kiện đăng nhập trong SIEM đã đủ để kết luận không có hoạt động đăng nhập chưa?",
      "options": [
        "Đủ; SIEM luôn thu thập mọi sự kiện Windows theo mặc định.",
        "Đủ; không có dòng log nghĩa là tài khoản chưa từng được sử dụng.",
        "Chưa; nhưng có thể khẳng định ngay mọi máy đều đã bị tấn công.",
        "Chưa; cần kiểm tra chính sách audit và việc thu thập log trước."
      ],
      "answer": 3,
      "explanation": "Thiếu log có thể liên quan tới audit, nguồn thu thập hoặc dữ liệu chưa có trong workspace. Phải kiểm tra độ phủ dữ liệu trước khi suy luận từ sự vắng mặt."
    },
    {
      "id": "shared-source-ip",
      "question": "Vì sao không nên coi IpAddress là định danh chắc chắn của một người?",
      "options": [
        "Một IP luôn chứng minh tất cả sự kiện thuộc cùng một người.",
        "Nó có thể là địa chỉ của proxy, NAT hoặc điểm ra dùng chung.",
        "Trường IP xác nhận sẵn người dùng đã vượt qua MFA.",
        "Mọi sự kiện đăng nhập luôn chứa cùng một IP nguồn hợp lệ."
      ],
      "answer": 1,
      "explanation": "Nhiều hoạt động có thể đi qua một điểm ra chung, và một số sự kiện thiếu dữ liệu mạng hữu ích. Cần đối chiếu tài khoản, máy, loại đăng nhập và bằng chứng khác."
    }
  ]
}
```
