# Bài 2: Tự động hóa đóng gói và phát hành Docker Image khi gắn Git Tag

## Giới thiệu
Bài tập này xây dựng một GitHub Actions workflow tự động hóa việc đóng gói và đẩy (push) Docker Image lên GitHub Container Registry (GHCR) mỗi khi có một Git Tag mới dạng `v*.*.*` được đẩy lên kho lưu trữ.

## Chức năng đã làm
- Cấu hình trigger `on.push.tags` với định dạng `v*.*.*`.
- Sử dụng `docker/login-action` để xác thực với GHCR.
- Sử dụng `docker/metadata-action` để tự động tạo Docker tags dựa trên semantic version của Git Tag.
- Sử dụng `docker/build-push-action` để build và push image.

## Hướng dẫn chạy/kiểm tra
1. Tạo tag cục bộ:
   `git tag v1.0.0`
2. Đẩy tag lên GitHub:
   `git push origin v1.0.0`
3. Kiểm tra kết quả tại tab **Actions** trên GitHub và danh sách gói trong **GitHub Packages**.