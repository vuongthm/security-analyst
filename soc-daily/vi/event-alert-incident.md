---
id: security-analyst:event-alert-incident
translationKey: security-analyst:event-alert-incident
slug: event-alert-incident
title: "Event, alert và incident: ba từ không nên dùng thay nhau"
description: "Một ghi chép độc lập về cách gọi tên quan sát, cảnh báo và sự cố để viết nhận định SOC rõ ràng hơn."
date: 2026-11-11
status: published
module: soc-daily
order: 1
topics: [soc, security]
tags: [soc, incident-response]
kind: note
level: beginner
lock: false
---

## Một sự kiện chưa phải một kết luận

**Event** là một điều quan sát được liên quan tới tài sản tính toán. Một lần đăng nhập, một tiến trình được tạo hoặc một kết nối được ghi nhận đều có thể là sự kiện. NIST SP 800-61 Rev. 3 dùng khái niệm sự kiện theo nghĩa rộng như vậy.

**Alert** là tín hiệu cần chú ý do một cơ chế giám sát tạo ra. Ví dụ, một quy tắc phát cảnh báo khi số lần đăng nhập thất bại vượt một ngưỡng. Định nghĩa và ý nghĩa của từng cảnh báo phụ thuộc hệ thống triển khai.

**Cybersecurity incident** liên quan đến việc thực sự hoặc sắp gây nguy hại trái phép cho tính bí mật, toàn vẹn, sẵn sàng; hoặc vi phạm hay đe dọa vi phạm luật, chính sách an ninh, quy trình bảo mật hoặc quy tắc sử dụng. Khi phân loại, cần căn cứ vào bằng chứng, tác động và tiêu chí của tổ chức. Không nên đổi mọi cảnh báo thành một sự cố chỉ để làm báo cáo trông nghiêm trọng hơn.

## Một ví dụ để tự đối chiếu

Giả sử hệ thống giám sát gửi cảnh báo về nhiều lần đăng nhập thất bại. Sau khi kiểm tra, nhóm xác nhận một dịch vụ vẫn dùng mật khẩu cũ sau đợt thay đổi đã được lên kế hoạch. Trong phạm vi bằng chứng này, chưa có cơ sở để kết luận kẻ tấn công đã chiếm tài khoản.

Đó là ví dụ minh họa, không phải quy tắc cho mọi hệ thống. Một mẫu đăng nhập giống nhau có thể có ý nghĩa khác trong ngữ cảnh khác.

## Cấu trúc ghi nhận phân tích

```text
Quan sát:
Nguồn dữ liệu:
Khoảng thời gian và múi giờ:
Tài sản, tài khoản liên quan:
Bằng chứng đã đối chiếu:
Giả thuyết còn mở:
Quyết định và lý do:
Người/nhóm tiếp nhận:
```

Cấu trúc ghi nhận này là cách tổ chức thông tin phân tích, không phải yêu cầu bắt buộc của NIST. Khi dùng trong công việc, cần theo quy trình thực tế của đơn vị.

## Điều muốn nhớ

Tách rõ quan sát, giả thuyết và kết luận giúp người đọc biết điều gì đã được kiểm chứng. Ghi lại cả sự thiếu hụt bằng chứng cũng có ích hơn việc viết một kết luận chắc chắn nhưng không có căn cứ.

## Tham khảo

- [NIST SP 800-61 Rev. 3: hướng dẫn ứng phó sự cố](https://csrc.nist.gov/pubs/sp/800/61/r3/final).

- [NIST: thuật ngữ event](https://csrc.nist.gov/glossary/term/event).
- [NIST: thuật ngữ cybersecurity incident](https://csrc.nist.gov/glossary/term/cybersecurity_incident).

```quiz
{
  "title": "Tự kiểm tra: event, alert và incident",
  "questions": [
    {
      "id": "event-meaning",
      "question": "Một event trong phạm vi bài có thể là điều gì?",
      "options": [
        "Chỉ một cuộc tấn công đã được xác nhận gây thiệt hại.",
        "Chỉ một báo cáo đã được trưởng nhóm phê duyệt.",
        "Một lần đăng nhập hoặc kết nối được quan sát và ghi nhận.",
        "Chỉ một cảnh báo do một sản phẩm SIEM cụ thể tạo ra."
      ],
      "answer": 2,
      "explanation": "Event là khái niệm rộng về điều quan sát được liên quan tới tài sản tính toán. Có sự kiện không đồng nghĩa đã có tấn công hay sự cố."
    },
    {
      "id": "alert-meaning",
      "question": "Một quy tắc giám sát tạo tín hiệu khi số lần đăng nhập thất bại vượt ngưỡng. Tín hiệu đó phù hợp nhất với khái niệm nào?",
      "options": [
        "Một bản ghi event thô, chưa được quy tắc đánh giá.",
        "Alert",
        "Một incident đã được xác minh đủ bằng chứng.",
        "Một giả thuyết của người phân tích, chưa có tín hiệu từ giám sát."
      ],
      "answer": 1,
      "explanation": "Alert thu hút sự chú ý tới một điều cần xem xét. Ý nghĩa cụ thể phụ thuộc quy tắc và hệ thống; nó không tự thay thế việc xác minh."
    },
    {
      "id": "incident-assessment",
      "question": "Khi cân nhắc phân loại một cybersecurity incident, cách tiếp cận nào phù hợp?",
      "options": [
        "Đối chiếu bằng chứng, tác động và tiêu chí xử lý của tổ chức.",
        "Chỉ dựa vào mức độ nghiêm trọng do sản phẩm gán.",
        "Chỉ dựa vào số lần lặp lại của cùng một cảnh báo.",
        "Chỉ dựa vào việc IP xuất hiện trong một danh sách cảnh báo."
      ],
      "answer": 0,
      "explanation": "Phân loại sự cố cần căn cứ và ngữ cảnh. Cách gọi phải phù hợp với điều đã được xác minh và quy trình xử lý của đơn vị."
    },
    {
      "id": "planned-password-change",
      "question": "Trong tình huống đã xác minh dịch vụ còn dùng mật khẩu cũ sau thay đổi có kế hoạch, điều nào có thể ghi nhận từ bằng chứng đó?",
      "options": [
        "Đã xác nhận tài khoản bị chiếm vì có nhiều lần đăng nhập thất bại.",
        "Đã xác nhận mọi cảnh báo đăng nhập trên hệ thống đều vô hại.",
        "Có thể bỏ qua việc ghi nhận kết quả vì đã biết một nguyên nhân hợp lệ.",
        "Chưa đủ cơ sở để kết luận tài khoản đã bị kẻ tấn công chiếm."
      ],
      "answer": 3,
      "explanation": "Kết luận cần giới hạn trong tình huống đã kiểm tra. Một nguyên nhân hợp lệ ở trường hợp này không chứng minh mọi cảnh báo tương tự đều vô hại."
    },
    {
      "id": "analysis-time-context",
      "question": "Khi ghi nhận các log để đối chiếu, thông tin nào giúp diễn giải mốc thời gian rõ ràng hơn?",
      "options": [
        "Khoảng thời gian và múi giờ của dữ liệu.",
        "Chỉ màu của dashboard khi chụp ảnh.",
        "Chỉ số lượng người có quyền xem báo cáo.",
        "Chỉ tên viết tắt của công cụ soạn thảo."
      ],
      "answer": 0,
      "explanation": "Ghi rõ khoảng thời gian và múi giờ giúp người đọc hiểu phạm vi quan sát và đối chiếu các nguồn. Đây là một trường trong cấu trúc ghi nhận của bài."
    },
    {
      "id": "fact-vs-hypothesis",
      "question": "Cách viết nào tách được quan sát và giả thuyết?",
      "options": [
        "Gọi ngay mọi đăng nhập thất bại là một cuộc tấn công đã thành công.",
        "Bỏ nguồn log để người đọc tập trung vào nhận định của tác giả.",
        "Ghi nhận số lần đăng nhập thất bại đã quan sát; nêu chiếm tài khoản là giả thuyết cần kiểm tra.",
        "Chỉ giữ kết luận và xóa mọi phần chưa chắc chắn."
      ],
      "answer": 2,
      "explanation": "Quan sát là điều dữ liệu cho thấy; giả thuyết là điều cần thêm bằng chứng để đánh giá. Tách chúng giúp người đọc không nhầm mức độ chắc chắn."
    },
    {
      "id": "recording-format",
      "question": "Cấu trúc ghi nhận phân tích được trình bày trong bài có phải biểu mẫu bắt buộc của NIST cho mọi tổ chức không?",
      "options": [
        "Có; mọi tổ chức bắt buộc dùng đúng các nhãn và thứ tự đó.",
        "Không; đó là cách tổ chức thông tin của bài, còn công việc phải theo quy trình đơn vị.",
        "Có; chỉ cần điền biểu mẫu là có thể bỏ bước kiểm chứng.",
        "Không; vì vậy không bao giờ cần ghi nguồn dữ liệu hoặc quyết định."
      ],
      "answer": 1,
      "explanation": "Bài phân biệt hướng dẫn tổ chức thông tin với một yêu cầu bắt buộc. Quy trình thực tế và tiêu chí của đơn vị vẫn phải được tuân thủ."
    },
    {
      "id": "insufficient-evidence",
      "question": "Khi bằng chứng còn thiếu, ghi nhận nào hữu ích hơn cho người tiếp nhận?",
      "options": [
        "Viết một kết luận chắc chắn để tránh câu hỏi bổ sung.",
        "Ẩn giới hạn dữ liệu để báo cáo có vẻ hoàn chỉnh hơn.",
        "Gộp quan sát và suy đoán thành một kết luận không có nguồn.",
        "Nêu điều đã biết, phần còn thiếu và giả thuyết cần kiểm tra tiếp."
      ],
      "answer": 3,
      "explanation": "Ghi rõ giới hạn bằng chứng giúp việc tiếp nhận và kiểm chứng tiếp theo có cơ sở. Sự chắc chắn trong cách diễn đạt không thay thế được bằng chứng."
    }
  ]
}
```
