# CrossPink — firmware downloads

Kho tải firmware CrossPink dành cho máy đọc sách Xteink. Repository này có lịch sử Git riêng, chỉ chứa tài liệu phát hành và giấy phép; mã nguồn firmware và lịch sử phát triển không được sao chép vào đây.

## Tải đúng firmware

Mở [bản ổn định mới nhất](https://github.com/ttakashinn/crosspink-releases/releases/latest) hoặc [toàn bộ phiên bản](https://github.com/ttakashinn/crosspink-releases/releases).

| Thiết bị | File cần tải |
| --- | --- |
| Xteink X3 / X4 | `firmware.bin` |
| Xteink X4 Pro | `firmware-x4pro.bin` |

Chỉ dùng asset được công bố cho thiết bị của bạn. Sticky, X4 Classic và Paper Mono có profile build trong dự án nguồn nhưng hiện không nằm trong 2 biến thể của workflow phát hành. Không nạp binary C3 cho X4 Pro hoặc ngược lại.

Tải cả file `.sha256` đi kèm. Trên macOS chạy `shasum -a 256 firmware.bin`; trên Linux chạy `sha256sum firmware.bin`; trên PowerShell chạy `Get-FileHash firmware.bin -Algorithm SHA256`. Đối chiếu đủ 64 ký tự với checksum đã tải. Với X4 Pro, thay tên file tương ứng.

## Cài từ thẻ SD

1. Giữ máy đủ pin và sao lưu dữ liệu đọc quan trọng trên thẻ.
2. Chép binary đúng thiết bị vào thẻ SD. Có thể dùng đầu đọc thẻ hoặc màn Truyền tập tin Wi-Fi của firmware đang dùng.
3. Nếu firmware hiện tại có mục này, mở **Cài đặt → Hệ thống → Cập nhật firmware từ thẻ SD**, chọn file và làm theo hướng dẫn trên máy.
4. Chờ cập nhật hoàn tất; không ngắt nguồn trong lúc ghi firmware. Kiểm tra lại phiên bản sau khi khởi động.

Giữ nguyên thư mục `/.crosspoint` để bảo toàn cấu hình và dữ liệu đọc. Việc đổi repo tải firmware không yêu cầu format thẻ hoặc xóa dữ liệu.

## OTA và cài qua USB

Firmware từ **`1.6.0-cp.7.3`** có địa chỉ OTA trỏ tới repo này. Repo nguồn `crosspink` hiện là private và không còn Release; máy cp.7.2 và cũ hơn không truy cập được địa chỉ OTA cũ. Các máy này cần cài thủ công bản mới đúng thiết bị qua thẻ SD nếu được hỗ trợ, hoặc qua USB tương thích, trước khi dùng được OTA hiện tại. Đọc [hướng dẫn chuyển OTA](OTA-MIGRATION.md).

Các file trên là **application image**, không phải image ghép đầy đủ bootloader/partition. Với X3/X4 đã có bootloader và bảng phân vùng CrossPink tương thích, có thể dùng esptool để ghi application vào `0x10000`:

```sh
esptool --chip esp32c3 --port YOUR_SERIAL_PORT --baud 921600 write-flash 0x10000 firmware.bin
```

Thay `YOUR_SERIAL_PORT` bằng cổng máy. Không dùng lệnh này như hướng dẫn cài lần đầu lên thiết bị/bảng phân vùng chưa xác định. Với máy khóa USB, chỉ dùng công cụ mở khóa khi nhà cung cấp xác nhận rõ firmware được hỗ trợ. Hướng dẫn SD/OTA chỉ áp dụng khi firmware hiện tại cung cấp chức năng đó.

## Font và giấy phép

Một số bản cũ có gói `crosspink-…-font-pack.zip`; giải nén theo README trong gói và giữ các giấy phép đi kèm. Manifest tải font trên thiết bị vẫn thuộc [CrossPoint Fonts](https://github.com/crosspoint-reader/crosspoint-fonts/releases), độc lập với repo firmware này.

Đọc [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) và [licenses/](licenses/). Giấy phép MIT của dự án gốc không thay thế GPL/LGPL, Apache, OFL và các điều kiện của thành phần được liên kết hoặc nhúng. Chia sẻ firmware miễn phí vẫn phải đáp ứng các điều kiện phân phối này.

Kho mã nguồn ứng dụng và SDK hiện được quản lý riêng tư. Repo này cung cấp firmware, checksum và thông báo giấy phép. Các mục “Source code (zip/tar.gz)” GitHub tự sinh trong repo này chỉ chứa tài liệu/giấy phép; chúng không phải mã nguồn firmware. Firmware công khai vẫn chứa giao diện web và mã máy có thể phân tích.

CrossPink kế thừa [CrossPoint Reader](https://github.com/crosspoint-reader/crosspoint-reader) và [FreeInk SDK](https://github.com/Free-Ink/freeink-sdk). Dự án không liên kết với nhà sản xuất thiết bị. Khi báo lỗi, cung cấp mẫu máy, phiên bản firmware và các bước tái lập; không đăng mật khẩu Wi-Fi, token hoặc dữ liệu cá nhân.
