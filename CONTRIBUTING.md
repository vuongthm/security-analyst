# Viết ghi chép trong security-analyst

Lộ trình nằm tại `soc-l1/learning-path.json` và `soc-l2/learning-path.json`. SOC L1 có đủ 14 module, 71 bài × Việt/Anh; SOC L2 đang nháp để bổ sung sau. `soc-daily/` dành cho ghi chép độc lập.

Bạn có thể viết bài ở bất kỳ thứ tự nào. Mỗi module có `vi/`, `en/`, `media/`; một bài có thể gắn nhiều chủ đề bằng `topics` và được nhiều lộ trình tham chiếu.

## Module hiện có

- `soc-l1/blue-team-introduction` — ID `blue-team-introduction`.
- `soc-l1/soc-team-internals` — ID `soc-team-internals`.
- `soc-l1/core-soc-solutions` — ID `core-soc-solutions`.
- `soc-l1/cyber-defence-frameworks` — ID `cyber-defence-frameworks`.
- `soc-l1/phishing-analysis` — ID `phishing-analysis`.
- `soc-l1/network-traffic-analysis` — ID `network-traffic-analysis`.
- `soc-l1/network-security-monitoring` — ID `network-security-monitoring`.
- `soc-l1/web-security-monitoring` — ID `web-security-monitoring`.
- `soc-l1/windows-security-monitoring` — ID `windows-security-monitoring`.
- `soc-l1/linux-security-monitoring` — ID `linux-security-monitoring`.
- `soc-l1/malware-concepts-for-soc` — ID `malware-concepts-for-soc`.
- `soc-l1/threat-analysis-tools` — ID `threat-analysis-tools`.
- `soc-l1/siem-triage-for-soc` — ID `siem-triage-for-soc`.
- `soc-l1/soc-level-1-capstone-challenges` — ID `soc-level-1-capstone-challenges`.
- `soc-daily` — ID `soc-daily`.

## Tạo bài nháp trong module

```bash
pnpm content:new article security-analyst new-note --module soc-daily
pnpm content:new article security-analyst new-note --module soc-daily --lang en
```

Ngày mặc định là ngày hiện tại theo giờ Việt Nam, không tiếp nối lịch của các khung nháp. Bản dịch kế thừa định danh, chủ đề, ngày và thứ tự. Khi đăng, điền mô tả/nội dung, sửa ngày thực tế rồi đổi `status: published`. Các file đã có khung có thể mở trực tiếp để viết, không cần tạo lại.

## Phân loại và lộ trình

- `module`: ID module trong manifest, độc lập với đường dẫn thư mục.
- `topics`: có thể gồm nhiều chủ đề đã đăng ký như `security`, `soc`, `networking`, `linux`, `cloud`, `ai`.
- `order`: thứ tự mặc định trong module, không phải ngày đăng.
- `id`, `translationKey`, `slug`: giữ ổn định, kể cả khi chuyển thư mục/repo; bản dịch dùng chung định danh.
- `learning-path.json → sections[].steps[].article`: chọn ID bài và thứ tự học riêng cho từng lộ trình. Không chép bài, không cần khai báo `learning` trong Markdown.
- `outline: true`: chủ động cho phép tên bản nháp hiện trong đề cương; thân bài/mô tả/media vẫn chưa công khai.

SOC L1, Pre Security và Cyber Security 101 đã chọn từng bài theo ID. Thêm bài mới vào module không tự đổi đề cương. Khi tự chọn chế độ `sections[].module`, path sẽ nhận thêm các bài của module.

Hướng dẫn đầy đủ: [CONTENT.md của website](https://github.com/vuongthm/vuongthm.github.io/blob/main/CONTENT.md).
