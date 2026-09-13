# Chuyển địa chỉ cập nhật OTA

## Tình trạng hiện tại

Các firmware đã công bố đến `1.6.0-cp.7.2` truy vấn `https://api.github.com/repos/ttakashinn/crosspink/releases/latest` và chỉ chấp nhận asset dưới `https://github.com/ttakashinn/crosspink/releases/download/`. Việc sao chép Release sang repo mới không thay đổi các chuỗi được nhúng trong máy.

Firmware từ **`1.6.0-cp.7.3`** đổi cả API và danh sách địa chỉ tải được chấp nhận sang `ttakashinn/crosspink-releases`. Repo phát hành tiếp tục công khai. Repo nguồn `crosspink` hiện là private và toàn bộ Release tại địa chỉ cũ đã được xóa, nên máy cp.7.2 và cũ hơn không còn cập nhật được qua OTA cũ.

## Lộ trình cập nhật

1. Máy đang ở cp.7.3 trở lên tiếp tục kiểm tra OTA tại repo phát hành.
2. Máy cp.7.2 và cũ hơn cần tải [bản ổn định mới nhất](https://github.com/ttakashinn/crosspink-releases/releases/latest) đúng thiết bị cùng file SHA-256, rồi cài thủ công qua thẻ SD nếu firmware hiện tại hỗ trợ hoặc qua USB tương thích. Xem [hướng dẫn cài](README.md).
3. Sau khi cài bản mới, kiểm tra phiên bản trên máy rồi sử dụng OTA như bình thường. GitHub không chuyển hướng một URL repo private thành URL repo phát hành khác chỉ vì các tag trùng nhau.

Workflow phát hành không tạo lại Release ở địa chỉ OTA cũ. Việc chuyển private không yêu cầu xóa dữ liệu đọc hoặc format thẻ.

Định dạng tag, so sánh phiên bản, kiểm tra SHA-256 và chọn binary theo thiết bị không đổi. OTA vẫn dùng bản stable từ `/releases/latest`; prerelease giữ nguyên trạng thái và không được dùng làm stable mới nhất.

## Cài lại một bản được build lại cùng số phiên bản

Nếu ghi chú Release nêu đây là bản build lại, máy đã cài cùng số phiên bản sẽ không được OTA báo có bản mới. Tải lại firmware và file SHA-256 đi kèm từ [Release 1.6.0-cp.7.3](https://github.com/ttakashinn/crosspink-releases/releases/tag/1.6.0-cp.7.3), thay bản tải trước đó trên thẻ rồi dùng **Cài đặt → Hệ thống → Cập nhật firmware từ thẻ SD**. X3/X4 dùng `firmware.bin`; X4 Pro dùng `firmware-x4pro.bin`. Có thể đổi tên file trên thẻ thành `crosspink-cp.7.3-rebuild-x3-x4.bin` hoặc `crosspink-cp.7.3-rebuild-x4pro.bin` để tránh chọn nhầm bản cũ.

Tag Git của bản đầu tiên được giữ nguyên khi build lại cùng phiên bản. Đối chiếu checksum của file vừa tải; không dùng checksum của bản tải cũ. Máy cp.7.2 và cũ hơn vẫn cần cài thủ công vì địa chỉ OTA được nhúng trong các bản này đã ngừng truy cập công khai.
