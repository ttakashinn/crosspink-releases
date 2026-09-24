# DISCLAIMER — PERSONAL-USE FIRMWARE

## ENGLISH

This is an independent, non-commercial firmware project created by its author for the author’s personal use. It is provided free of charge, “AS IS” and “AS AVAILABLE,” without any warranty or promise of support, maintenance, updates, compatibility, security, reliability, or fitness for a particular purpose.

Installing or using custom firmware is voluntary and at your own risk. The process may fail, prevent the device from starting, erase or corrupt data, affect connected accessories, cause malfunctions, or damage the device. Before proceeding, confirm that the firmware is intended for your exact device model and hardware revision, read the installation instructions, and back up your data. You are responsible for installation, backups, recovery, and the consequences of using the firmware.

The author disclaims responsibility for loss or damage arising from downloading, installing, modifying, or using this firmware, including device damage, data loss, loss of use, or consequential loss.

No warranty or technical support is offered. If you do not accept these risks, do not install or use this firmware.

## TUYÊN BỐ MIỄN TRỪ TRÁCH NHIỆM — FIRMWARE DÙNG CÁ NHÂN

## TIẾNG VIỆT

Đây là firmware thuộc một dự án độc lập, phi thương mại, do tác giả tạo ra cho nhu cầu sử dụng cá nhân của chính tác giả. Firmware được cung cấp miễn phí, theo hiện trạng (“NGUYÊN TRẠNG”) và khi có sẵn, không kèm bảo đảm hoặc cam kết về hỗ trợ, bảo trì, cập nhật, khả năng tương thích, bảo mật, độ tin cậy hay tính phù hợp cho một mục đích cụ thể.

Việc cài đặt hoặc sử dụng firmware tùy chỉnh là tự nguyện và do bạn tự chịu rủi ro. Quá trình này có thể thất bại, khiến thiết bị không khởi động được, xóa hoặc làm hỏng dữ liệu, ảnh hưởng đến phụ kiện kết nối, gây trục trặc hoặc làm hỏng thiết bị. Trước khi thực hiện, hãy xác nhận firmware dành đúng mẫu thiết bị và phiên bản phần cứng của bạn, đọc hướng dẫn cài đặt và sao lưu dữ liệu. Bạn tự chịu trách nhiệm về việc cài đặt, sao lưu, khôi phục và các hậu quả phát sinh từ việc sử dụng firmware.

Tác giả từ chối trách nhiệm đối với mất mát hoặc thiệt hại phát sinh từ việc tải xuống, cài đặt, sửa đổi hoặc sử dụng firmware này, bao gồm hỏng thiết bị, mất dữ liệu, mất khả năng sử dụng hoặc thiệt hại phát sinh tiếp theo.

Tác giả không cung cấp bảo hành hoặc hỗ trợ kỹ thuật. Nếu bạn không chấp nhận các rủi ro này, đừng cài đặt hoặc sử dụng firmware.

---

# CrossPink — firmware downloads

Kho tải firmware CrossPink dành cho máy đọc sách Xteink. Repository này có lịch sử Git riêng, chỉ chứa tài liệu phát hành và giấy phép; mã nguồn firmware và lịch sử phát triển không được sao chép vào đây.

## Tải đúng firmware

Mở [bản ổn định mới nhất](https://github.com/ttakashinn/crosspink-releases/releases/latest) hoặc [toàn bộ phiên bản](https://github.com/ttakashinn/crosspink-releases/releases).

| Kênh | Thiết bị | File cần tải |
| --- | --- | --- |
| Full | Xteink X3 / X4 | `firmware.bin` |
| Full | Xteink X4 Pro | `firmware-x4pro.bin` |
| Light | Xteink X3 / X4 | `firmware-light.bin` |
| Light | Xteink X4 Pro | `firmware-light-x4pro.bin` |

Chỉ dùng asset được công bố cho thiết bị của bạn. Sticky, X4 Classic và Paper Mono có profile build trong dự án nguồn nhưng hiện không nằm trong 2 biến thể của workflow phát hành. Không nạp binary C3 cho X4 Pro hoặc ngược lại.

Kiểm tra SHA-256 là bước tùy chọn. Nếu muốn kiểm tra, tải file `.sha256` đi kèm; trên macOS chạy `shasum -a 256 FILE.bin`, trên Linux chạy `sha256sum FILE.bin`, hoặc trên PowerShell chạy `Get-FileHash FILE.bin -Algorithm SHA256`. Thay `FILE.bin` bằng tên file đã tải và đối chiếu đủ 64 ký tự với file checksum tương ứng.

## Cài từ thẻ SD

1. Giữ máy đủ pin và sao lưu dữ liệu đọc quan trọng trên thẻ.
2. Chép binary đúng thiết bị vào thẻ SD. Có thể dùng đầu đọc thẻ hoặc màn Truyền tập tin Wi-Fi của firmware đang dùng.
3. Nếu firmware hiện tại có mục này, mở **Cài đặt → Hệ thống → Cập nhật firmware từ thẻ SD**, chọn file và làm theo hướng dẫn trên máy.
4. Chờ cập nhật hoàn tất; không ngắt nguồn trong lúc ghi firmware. Kiểm tra lại phiên bản sau khi khởi động.

Giữ nguyên thư mục `/.crosspoint` để bảo toàn cấu hình và dữ liệu đọc. Không format thẻ SD khi cập nhật. Xem [hướng dẫn cài đặt](INSTALLATION_GUIDE.txt) để chọn đúng file và cách cài phù hợp với firmware hiện tại.

## Cài qua USB

Các file trên là **application image**, không phải image ghép đầy đủ bootloader/partition. Với X3/X4 đã có bootloader và bảng phân vùng CrossPink tương thích, có thể dùng esptool để ghi application vào `0x10000`:

```sh
esptool --chip esp32c3 --port YOUR_SERIAL_PORT --baud 921600 write-flash 0x10000 firmware.bin
```

Thay `YOUR_SERIAL_PORT` bằng cổng máy. Không dùng lệnh này như hướng dẫn cài lần đầu lên thiết bị/bảng phân vùng chưa xác định. Với máy khóa USB, chỉ dùng công cụ mở khóa khi nhà cung cấp xác nhận rõ firmware được hỗ trợ. Hướng dẫn SD/OTA chỉ áp dụng khi firmware hiện tại cung cấp chức năng đó.

## Font và giấy phép

Một số bản cũ có gói `crosspink-…-font-pack.zip`; giải nén theo README trong gói và giữ các giấy phép đi kèm. Manifest tải font trên thiết bị vẫn thuộc [CrossPoint Fonts](https://github.com/crosspoint-reader/crosspoint-fonts/releases), độc lập với repo firmware này.

Đọc [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) và [licenses/](licenses/). Giấy phép MIT của dự án gốc không thay thế GPL/LGPL, Apache, OFL và các điều kiện của thành phần được liên kết hoặc nhúng. Chia sẻ firmware miễn phí vẫn phải đáp ứng các điều kiện phân phối này.

Repo này cung cấp firmware, checksum và thông báo giấy phép. Các mục “Source code (zip/tar.gz)” GitHub tự sinh trong repo này chỉ chứa tài liệu/giấy phép; chúng không phải mã nguồn firmware. Firmware công khai vẫn chứa giao diện web và mã máy có thể phân tích.

CrossPink kế thừa [CrossPoint Reader](https://github.com/crosspoint-reader/crosspoint-reader) và [FreeInk SDK](https://github.com/Free-Ink/freeink-sdk). Dự án không liên kết với nhà sản xuất thiết bị. Khi báo lỗi, cung cấp mẫu máy, phiên bản firmware và các bước tái lập; không đăng mật khẩu Wi-Fi, token hoặc dữ liệu cá nhân.
