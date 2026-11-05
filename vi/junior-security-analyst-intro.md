---
id: "soc-notes:junior-security-analyst-intro"
translationKey: "soc-notes:junior-security-analyst-intro"
title: "Junior Security Analyst Intro"
description: "Phân biệt cảnh báo, sự kiện và sự cố; bắt đầu triage bằng bằng chứng."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 0
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: junior-security-analyst-intro
---

## Một vị trí, nhiều nguồn thông tin

SOC kết hợp con người, quy trình và công cụ để giám sát và xử lý sự kiện bảo mật. Analyst mới thường bắt đầu bằng [triage](glossary:triage "Phân loại ban đầu để xác định ưu tiên và bước xử lý tiếp theo."): kiểm tra cảnh báo, xác định ngữ cảnh, ghi nhận bằng chứng và chuyển cấp theo quy trình của nhóm.

SIEM có thể gom sự kiện từ nhiều hệ thống. EDR cung cấp quan sát trên endpoint. Hai công cụ bổ sung cho nhau; một dashboard không thay thế toàn bộ cuộc điều tra.

## Cảnh báo chưa phải kết luận

Giả sử một tài khoản đăng nhập thất bại nhiều lần rồi thành công từ một địa chỉ mới. Đây là lý do cần kiểm tra, chưa đủ để khẳng định bị chiếm tài khoản. Hãy đối chiếu thời gian, thiết bị, lịch sử người dùng, MFA và log liên quan.

Tách ba cột trong ghi chép: điều đã quan sát, giả thuyết và điều còn thiếu. Giữ nguồn log gốc và ghi lại bộ lọc đã dùng để người khác có thể tái dựng phân tích.

## Triage có giới hạn rõ ràng

1. Xác định tài sản và người dùng liên quan.
2. Kiểm tra tính đầy đủ của dữ liệu và múi giờ.
3. Đánh giá tác động và độ tin cậy của tín hiệu.
4. Bổ sung bằng chứng, rồi đóng hoặc chuyển cấp với lý do rõ ràng.

Không tự ý cô lập hệ thống sản xuất khi chưa có thẩm quyền và quy trình phù hợp. Ghi chép này là phần nhập môn; thao tác thực hành cần diễn ra trong môi trường được phép.

## Nguồn tham khảo

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Tự kiểm tra kiến thức",
  "questions": [
    {
      "id": "q1",
      "question": "Bước triage nào có ích trước khi kết luận?",
      "options": [
        "Đối chiếu tài sản, thời gian và bằng chứng liên quan",
        "Chặn mọi máy ngay khi thấy một alert",
        "Xem cảnh báo là bằng chứng cuối cùng"
      ],
      "answer": 0,
      "explanation": "Triage xây ngữ cảnh và đánh giá độ tin cậy của tín hiệu."
    },
    {
      "id": "q2",
      "question": "SIEM và EDR liên hệ thế nào?",
      "options": [
        "Cung cấp các góc quan sát bổ sung cho nhau",
        "Hai tên gọi của đúng một loại log",
        "EDR thay thế mọi nguồn log mạng"
      ],
      "answer": 0,
      "explanation": "SIEM tổng hợp sự kiện, trong khi EDR tập trung vào endpoint."
    },
    {
      "id": "q3",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q4",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q5",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q6",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q7",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q8",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q9",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    },
    {
      "id": "q10",
      "question": "Nhật ký phân tích nên tách những phần nào?",
      "options": [
        "Quan sát, giả thuyết và thông tin còn thiếu",
        "Chỉ tên công cụ và người thao tác",
        "Chỉ kết luận chắc chắn"
      ],
      "answer": 0,
      "explanation": "Tách bằng chứng khỏi suy luận giúp đồng đội kiểm tra và tiếp tục điều tra."
    }
  ]
}
```
