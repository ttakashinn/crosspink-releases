# Chuyển địa chỉ cập nhật OTA

## Tình trạng hiện tại

Các firmware đã công bố đến `1.6.0-cp.7.2` truy vấn `https://api.github.com/repos/ttakashinn/crosspink/releases/latest` và chỉ chấp nhận asset dưới `https://github.com/ttakashinn/crosspink/releases/download/`. Việc sao chép Release sang repo mới không thay đổi các chuỗi được nhúng trong máy.

Phiên bản chuyển tiếp được chọn là **`1.6.0-cp.7.3`**. Firmware từ bản này đổi cả API và danh sách địa chỉ tải được chấp nhận sang `ttakashinn/crosspink-releases`. Kiểm tra [danh sách Releases](https://github.com/ttakashinn/crosspink-releases/releases) để tải bản đã công bố; các binary cp.7.2 và cũ hơn được sao chép sang kho mới vẫn giữ nguyên checksum và địa chỉ OTA cũ.

## Lộ trình cập nhật

1. Repo `crosspink` tiếp tục public để firmware cũ vẫn truy cập được đường OTA và mã nguồn tương ứng.
2. Bản chuyển tiếp cp.7.3 đã có mặt ở cả repo cũ và repo phát hành, với cùng binary và checksum, để máy cũ tải được nó từ địa chỉ đã ghim. Sau khi cài cp.7.3, máy sẽ kiểm tra các bản tiếp theo tại repo phát hành.
3. Kiểm tra trên X3/X4 và X4 Pro: tải từ repo cũ, cài, rồi truy vấn repo mới và tải đúng asset/checksum. Chỉ sau đó mới chốt việc chuyển private và cách hỗ trợ người còn ở firmware cũ.
4. Sau khi repo nguồn trở thành private, máy chưa cài bản chuyển tiếp sẽ cần cập nhật thủ công từ SD hoặc USB tương thích. GitHub không chuyển hướng một URL repo private thành URL repo phát hành khác chỉ vì các tag trùng nhau.

Không có mốc chuyển private tự động hoặc thời hạn ép cập nhật trong thay đổi này. Điều kiện giấy phép/mã nguồn phải được xử lý riêng trước khi ẩn repo nguồn.

Định dạng tag, so sánh phiên bản, kiểm tra SHA-256 và chọn binary theo thiết bị không đổi. OTA vẫn dùng bản stable từ `/releases/latest`; prerelease giữ nguyên trạng thái và không được dùng làm stable mới nhất.

## Cài lại một bản được build lại cùng số phiên bản

Nếu ghi chú Release nêu đây là bản build lại, máy đã cài cùng số phiên bản sẽ không được OTA báo có bản mới. Tải lại firmware và file SHA-256 đi kèm từ [Release 1.6.0-cp.7.3](https://github.com/ttakashinn/crosspink-releases/releases/tag/1.6.0-cp.7.3), thay bản tải trước đó trên thẻ rồi dùng **Cài đặt → Hệ thống → Cập nhật firmware từ thẻ SD**. X3/X4 dùng `firmware.bin`; X4 Pro dùng `firmware-x4pro.bin`. Có thể đổi tên file trên thẻ thành `crosspink-cp.7.3-rebuild-x3-x4.bin` hoặc `crosspink-cp.7.3-rebuild-x4pro.bin` để tránh chọn nhầm bản cũ.

Bản build lại ghi rõ commit mã nguồn trong ghi chú Release. Tag Git của bản đầu tiên được giữ nguyên để bảo toàn lịch sử; hãy dùng liên kết mã nguồn tương ứng trong ghi chú khi cần lấy đúng mã của bản build lại. Máy cp.7.2 vẫn nhận cp.7.3 là bản mới và tải qua địa chỉ OTA cũ.
