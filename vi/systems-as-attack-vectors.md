---
id: "soc-notes:systems-as-attack-vectors"
translationKey: "soc-notes:systems-as-attack-vectors"
title: "Systems as Attack Vectors"
description: "Kết nối tài sản, cấu hình và log để hiểu bề mặt tấn công của hệ thống."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 3
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: systems-as-attack-vectors
---

## Biết hệ thống trước khi biết cảnh báo

Một dịch vụ công khai, cấu hình quyền sai hoặc phần mềm chưa cập nhật có thể tạo đường vào hệ thống. Tác động phụ thuộc tài sản, dữ liệu, quyền và khả năng di chuyển đến các thành phần khác.

## Lập bản đồ quan sát

Với một ứng dụng nhỏ, ghi lại dịch vụ nào được mở, tài khoản nào quản trị, log nào được thu thập và ai sở hữu hệ thống. Nhìn vào cả kết nối mạng lẫn hành vi trên endpoint; SIEM và EDR trả lời những câu hỏi khác nhau.

## Lỗ hổng không tự chứng minh đã bị khai thác

Thông tin phiên bản hoặc kết quả quét là đầu mối. Để phân tích một sự cố, cần đối chiếu bằng chứng như tiến trình bất thường, thay đổi tệp, hoạt động xác thực và kết nối liên quan. Việc không nhìn thấy một hành vi cũng có thể do thiếu log.

## Ưu tiên theo rủi ro thực tế

Xem xét khả năng bị tiếp cận, mức quyền và ảnh hưởng đến nghiệp vụ. Khắc phục cần có chủ sở hữu, kế hoạch thay đổi và cách kiểm tra lại. Chỉ thu thập dữ liệu trong phạm vi được cho phép và giữ nguyên bằng chứng cần thiết.

## Nguồn tham khảo

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Tự kiểm tra kiến thức",
  "questions": [
    {
      "id": "q1",
      "question": "Phát hiện phiên bản có lỗ hổng tự nó chứng minh gì?",
      "options": [
        "Có một đầu mối rủi ro cần đối chiếu thêm",
        "Hệ thống chắc chắn đã bị khai thác",
        "Mọi log đều không cần nữa"
      ],
      "answer": 0,
      "explanation": "Tình trạng lỗ hổng và bằng chứng khai thác là hai việc khác nhau."
    },
    {
      "id": "q2",
      "question": "Không tìm thấy một hành vi trong log có thể có nghĩa gì?",
      "options": [
        "Chắc chắn SIEM bị tắt",
        "Có thể thiếu khả năng quan sát, chưa thể kết luận hành vi không xảy ra",
        "Chắc chắn hệ thống an toàn"
      ],
      "answer": 1,
      "explanation": "Cần kiểm tra phạm vi thu thập và độ đầy đủ của dữ liệu."
    },
    {
      "id": "q3",
      "question": "Ưu tiên khắc phục nên xét điều gì?",
      "options": [
        "Chỉ tên sản phẩm bảo mật",
        "Khả năng tiếp cận, quyền và tác động nghiệp vụ",
        "Chỉ số lượng ảnh chụp màn hình"
      ],
      "answer": 1,
      "explanation": "Rủi ro gắn với hệ thống thực tế; thay đổi cần có chủ sở hữu và kiểm tra lại."
    }
  ]
}
```
