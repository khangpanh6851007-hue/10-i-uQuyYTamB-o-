# Phật Pháp Tôn Nghiêm — Ultra 2026

Website tĩnh tiếng Việt về học tập và thực hành Phật pháp, giao diện tối với tông vàng kim và xanh Phật giáo. Dự án được thiết kế để chạy trên GitHub Pages và trình duyệt di động.

## Tính năng

### Nội dung và công cụ có sẵn
- 10 điều Quy y Tam Bảo.
- 10 điều ngăn cấm.
- Công cụ tính điểm nghiệp lực minh họa (không phải phép đo nghiệp quả thực tế).
- Đọc nội dung bằng SpeechSynthesis của trình duyệt.
- Thư viện tham khảo kinh Phật và pháp thoại.
- Lịch tu tập 365 ngày và đánh dấu ngày thực hành.
- Bộ đếm tụng kinh, Chú Đại Bi và Chú Vãng Sanh.
- Nhật ký công đức và hồi hướng.
- Thời khóa buổi sáng và buổi tối.
- Thống kê tiến độ và xuất dữ liệu JSON.
- Giao diện responsive cho điện thoại, máy tính bảng và máy tính.

## Chạy thử

Mở `index.html` bằng trình duyệt hiện đại hoặc chạy máy chủ tĩnh trong thư mục dự án, ví dụ:

```bash
python -m http.server 8000
```

Sau đó truy cập `http://localhost:8000`.

## Triển khai GitHub Pages

1. Tạo repository trên GitHub.
2. Đưa `index.html`, `README.md` và thư mục `.github/workflows/` lên nhánh `main`.
3. Mở **Settings → Pages**.
4. Trong **Build and deployment**, chọn **Deploy from a branch** nếu muốn tự cấu hình theo nhánh; hoặc để workflow GitHub Actions bên dưới triển khai tự động.
5. Nếu dùng workflow, vào **Settings → Actions → General**, cho phép workflow có quyền đọc và ghi nếu chính sách repository yêu cầu; workflow khai báo quyền `pages: write` và `id-token: write`.
6. Push commit lên `main`. Mở tab **Actions** để theo dõi lần triển khai.
7. Khi hoàn tất, địa chỉ website thường có dạng `https://TEN-TAI-KHOAN.github.io/TEN-REPOSITORY/`.

## Giọng đọc nam và nữ

Trang sử dụng Web Speech API (`speechSynthesis`) có sẵn trong trình duyệt/hệ điều hành. Danh sách giọng phụ thuộc vào thiết bị và gói giọng đã cài. Bộ lọc nam/nữ chỉ suy đoán từ tên giọng vì trình duyệt không cung cấp trường giới tính chuẩn. Nếu thiết bị không có giọng tiếng Việt phù hợp, hãy cài thêm giọng đọc tiếng Việt trong cài đặt hệ điều hành hoặc thử trình duyệt khác.

Đây không phải dịch vụ tạo giọng AI đám mây; website không tải giọng đọc từ máy chủ.

## Lưu trữ dữ liệu

Các bộ đếm, ngày đã đánh dấu và nhật ký được lưu bằng `localStorage` trên trình duyệt hiện tại. Dữ liệu không tự đồng bộ giữa các thiết bị hoặc trình duyệt. Dùng nút **Sao lưu dữ liệu tu tập** để xuất tệp JSON và lưu giữ bản sao.

## Lưu ý nội dung

Các danh mục kinh/pháp thoại trong bản hiện tại là mục tham khảo và gợi ý chủ đề. Vui lòng đối chiếu văn bản, bản dịch và nguồn xuất bản đáng tin cậy theo truyền thống tu học của bạn. Điểm số nghiệp lực trong ứng dụng chỉ là quy ước minh họa, không đại diện cho giáo lý hay phán quyết tôn giáo.

## Cấu trúc dự án

```text
.
├── index.html
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml
```

## Giấy phép

Chưa chỉ định giấy phép. Nếu muốn người khác sử dụng, sửa đổi hoặc phân phối mã nguồn, hãy bổ sung tệp `LICENSE` với giấy phép phù hợp.
