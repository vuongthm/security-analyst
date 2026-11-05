---
id: "field-notes:soc-first-investigation"
translationKey: "field-notes:soc-first-investigation"
title: "SOC: từ một cảnh báo đến một giả thuyết"
description: "Phân biệt tín hiệu, bằng chứng và kết luận khi bắt đầu tìm hiểu công việc phân tích bảo mật."
topics: ["soc", "security"]
tags: ["soc", "security"]
date: "2026-11-03"
kind: "guide"
level: "beginner"
featured: true
---

## Cảnh báo là điểm bắt đầu

Một cảnh báo không tự động đồng nghĩa với một cuộc tấn công. Nó cho biết một điều kiện được cấu hình đã xảy ra. Nhiệm vụ tiếp theo là xây ngữ cảnh và kiểm chứng giả thuyết.

## Năm câu hỏi đầu tiên

1. Tài khoản hoặc thiết bị nào liên quan?
2. Sự kiện xảy ra lúc nào, với múi giờ nào?
3. Dữ liệu nào hỗ trợ cảnh báo?
4. Hành vi này khác thường so với điều gì?
5. Cần thêm nguồn bằng chứng nào?

## Dựng một timeline

Sắp xếp log xác thực, truy cập ứng dụng và kết nối mạng theo thời gian. Chuẩn hóa múi giờ trước khi ghép sự kiện. Giữ lại log gốc; ghi rõ phép lọc và nguồn dữ liệu.

```text
09:12 UTC  authentication failure
09:14 UTC  authentication success
09:16 UTC  new remote session
```

Đây là ví dụ minh họa, chưa đủ để kết luận tài khoản bị xâm nhập.

## Viết kết luận có giới hạn

Tách phần đã quan sát, phần suy luận và phần chưa biết. Ghi lại lý do đóng cảnh báo hoặc chuyển cấp điều tra. Một báo cáo tốt cho phép người khác tái dựng cách bạn đi đến kết luận.

## Đọc thêm

[MITRE ATT&CK](https://attack.mitre.org/) cung cấp một ngôn ngữ chung về chiến thuật và kỹ thuật. Dùng framework để tổ chức bằng chứng, không để thay thế bằng chứng.

```quiz
{
  "title": "Tự kiểm tra kiến thức",
  "questions": [
    {
      "id": "q1",
      "question": "Một cảnh báo tự nó chứng minh điều gì?",
      "options": [
        "Một điều kiện phát hiện đã được kích hoạt",
        "Chắc chắn đã có xâm nhập",
        "Chắc chắn tài khoản đã bị chiếm"
      ],
      "answer": 0,
      "explanation": "Cần bổ sung ngữ cảnh và bằng chứng trước khi kết luận có sự cố."
    },
    {
      "id": "q2",
      "question": "Trước khi ghép log vào timeline, cần chú ý điều gì?",
      "options": [
        "Xóa log không khớp giả thuyết",
        "Chỉ giữ dòng có màu đỏ",
        "Chuẩn hóa múi giờ và giữ nguồn dữ liệu"
      ],
      "answer": 2,
      "explanation": "Múi giờ không thống nhất có thể đảo thứ tự sự kiện; log gốc giúp kiểm chứng lại."
    }
  ]
}
```
