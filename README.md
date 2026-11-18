# Time Align — Car Audio Delay Calculator

Công cụ web tính thời gian trễ (time alignment) cho hệ thống âm thanh xe hơi từ các file impulse response `.wav` đo bằng HouseCurve/REW.

Toàn bộ xử lý diễn ra trong trình duyệt, không upload file lên server.

## Tính năng

- Kéo thả nhiều file `.wav` cùng lúc, chọn một file làm reference.
- Phát hiện onset (khuyến nghị) hoặc peak của impulse response.
- Tính delay tương đối so với loa reference.
- Xuất giá trị nhập vào DSP theo ms, cm và số sample.
- Tự động làm tròn theo bước DSP: 0.01 ms, 0.02 ms, 0.1 ms, 1 cm hoặc 1 sample.
- Phát hiện polarity đảo pha so với reference.
- Hỗ trợ chế độ active/full-range và 2-way passive cho loa sub.
- Tuỳ chỉnh ngưỡng onset, smoothing, tốc độ âm thanh mặc định 343 m/s.
- Copy kết quả dạng TSV hoặc export CSV.
- Có bản tiếng Việt và tiếng Anh trong `versions/`.

## Sử dụng

Mở `index.html` trực tiếp trong trình duyệt, hoặc chạy một static server:

```bash
python3 -m http.server 8000
```

Sau đó mở <http://localhost:8000>.

Kéo thả các file impulse response, chọn reference, chọn phương pháp đo và nhập giá trị delay hiển thị vào DSP.

## Cấu trúc

```
index.html          # Ứng dụng chính
deploy/index.html   # Bản deploy trên Netlify
versions/           # Các phiên bản tiếng Việt / tiếng Anh / compact
im/                 # File WAV mẫu (FL, FR, RL, RR, sub)
netlify.toml        # Cấu hình Netlify (publish = deploy)
```

## Lưu ý

- Chỉ tính delay tương đối; cần đo tất cả loa trong cùng một phiên, cùng vị trí micro.
- Polarity chỉ mang tính tương đối so với reference — kiểm tra lại trước khi đấu dây loa.
- Delay tuyệt đối không có ý nghĩa nếu các phép đo không cùng điều kiện.
