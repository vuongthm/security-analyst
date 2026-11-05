---
id: "soc-notes:soc-role-in-blue-team"
translationKey: "soc-notes:soc-role-in-blue-team"
title: "SOC Role in Blue Team"
description: "Hiểu cách SOC phối hợp với đội phản ứng sự cố, quản trị hệ thống và threat intelligence."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 1
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: soc-role-in-blue-team
---

## Blue Team rộng hơn một phòng giám sát

Blue Team là cách gọi các hoạt động phòng thủ. SOC tập trung vào giám sát và phân tích, nhưng còn cần đội vận hành hạ tầng, quản trị danh tính, ứng cứu sự cố và các đơn vị sở hữu tài sản. Trách nhiệm cụ thể phụ thuộc tổ chức.

Một cảnh báo đáng chú ý có thể bắt đầu ở SIEM, được làm giàu bằng dữ liệu endpoint từ EDR, rồi chuyển cho người có thẩm quyền điều phối ứng phó. Giao tiếp rõ ràng giúp tránh việc nhiều nhóm cùng thay đổi một hệ thống mà không biết nhau đang làm gì.

## Chuyển cấp bằng một gói thông tin có ích

Báo cáo nên chỉ rõ tài sản, thời gian và múi giờ, bằng chứng quan trọng, mức ảnh hưởng có thể có, điều đã kiểm tra và câu hỏi cần nhóm tiếp theo xử lý. Một mức độ ưu tiên cao cần có lý do; không chỉ vì cảnh báo có màu đỏ.

## Cải tiến sau cuộc điều tra

Nếu tín hiệu là nhiễu, cân nhắc điều chỉnh rule trong quy trình kiểm soát thay đổi. Nếu thiếu log, ghi rõ khoảng trống quan sát. Nếu cần một hành động lặp lại, viết thành workbook có điều kiện và người chịu trách nhiệm. Mục tiêu là làm lần điều tra tiếp theo rõ ràng hơn.

## Nguồn tham khảo

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Tự kiểm tra kiến thức",
  "questions": [
    {
      "id": "q1",
      "question": "Blue Team có đồng nghĩa chỉ với SOC không?",
      "options": [
        "Có, không cần đội vận hành",
        "Không, còn có nhiều vai trò phòng thủ và chủ sở hữu hệ thống",
        "Có, mọi công việc đều ở một dashboard"
      ],
      "answer": 1,
      "explanation": "SOC phối hợp với các đội khác; mô hình trách nhiệm phụ thuộc tổ chức."
    },
    {
      "id": "q2",
      "question": "Một gói chuyển cấp nên có gì?",
      "options": [
        "Chỉ một câu: có hacker",
        "Bằng chứng, tác động có thể có và điều đã kiểm tra",
        "Chỉ ảnh màu đỏ của cảnh báo"
      ],
      "answer": 1,
      "explanation": "Thông tin này giúp nhóm tiếp theo tiếp tục điều tra mà không phải đoán bối cảnh."
    },
    {
      "id": "q3",
      "question": "Khi một rule tạo nhiều nhiễu thì nên làm gì?",
      "options": [
        "Đánh giá và điều chỉnh qua quy trình kiểm soát thay đổi",
        "Âm thầm xóa toàn bộ nguồn log",
        "Mặc định coi mọi alert là sự cố"
      ],
      "answer": 0,
      "explanation": "Tuning cần giữ khả năng phát hiện và có cách kiểm tra lại."
    }
  ]
}
```
