# OpenSea Auto Mint Bot GUI


> Tool sử dụng OpenSea Drops API để lấy dữ liệu mint và calldata. Hãy kiểm tra điều khoản OpenSea, điều kiện của collection và quy định tại nơi bạn sinh sống trước khi sử dụng.

## Tính năng

- Giao diện desktop tiếng Việt, giao diện tối.
- Chọn mạng **Base** hoặc **Robinhood Chain**.
- Lấy thông tin OpenSea Drop theo collection slug: tên, supply, các phase, thời gian mở, giá và giới hạn mỗi ví.
- Tự chọn thời điểm phase gần nhất và bắt đầu thử mint từ khoảng 5 giây trước giờ mở; tiếp tục thử trong tối đa 30 giây sau giờ mở.
- Mint ngay không chờ, hoặc dừng chế độ tự động.
- Gửi log giao dịch và đường dẫn explorer sau khi gửi transaction.

## Tải và chạy

Tải `Bot_mint_NFT.exe` từ mục **Releases** của repository và chạy trên Windows.


## Cách sử dụng

1. Chọn **Chain**.
2. Nhập private key của một ví dùng riêng cho mint (burner wallet).
3. Nhập collection slug của OpenSea, ví dụ `test-mint-20675216`.
4. Nhập OpenSea API Key.
5. Nếu muốn, nhập NFT contract address. Trường này chỉ hiển thị trong thông tin; yêu cầu mint được gửi theo slug.
6. Chọn số lượng ở **Quantity**.
7. Chọn **Lấy thông tin Drop + Phase** để kiểm tra dữ liệu và thời gian các phase.
8. Chọn **Auto Mint** để chạy theo giờ mở, **Mint ngay** để thử ngay, hoặc **Dừng** để ngắt chế độ tự động.

API key được gửi trong header `X-API-KEY` tới OpenSea API. Khi mint, ứng dụng yêu cầu calldata từ OpenSea, ký transaction bằng private key đã nhập và gửi transaction qua RPC của chain đã chọn. Giao dịch sau khi gửi lên blockchain không thể được thu hồi bằng nút Dừng.

## Mạng được cấu hình

| Mạng | Chain ID | RPC | Explorer |
| --- | ---: | --- | --- |
| Base | 8453 | `https://mainnet.base.org` | [Basescan](https://basescan.org) |
| Robinhood Chain | 4663 | `https://rpc.mainnet.chain.robinhood.com` | [Robinhood Chain Explorer](https://robinhoodchain.blockscout.com) |

## Bảo mật và rủi ro

- **Không dùng ví chính hoặc ví chứa tài sản có giá trị.** Chỉ nhập private key của ví riêng với số dư giới hạn đủ cho mint và phí gas.
- Private key được dùng tại máy để ký giao dịch; không nhập key vào issue, README, log, ảnh chụp màn hình hay repository. Không chia sẻ file cấu hình chứa key.
- Chỉ tải file thực thi từ nguồn mà bạn tin tưởng. Người phát hành nên cung cấp checksum và build/release minh bạch.
- Mint có thể thất bại do phase chưa mở/đã đóng (HTTP 409), ví không đủ điều kiện hoặc hết supply/limit (HTTP 422), RPC/API lỗi, hoặc giao dịch bị từ chối.
- Giao dịch có thể tiêu tốn gas và khoản mint có thể không hoàn lại. Kiểm tra chain, slug, số lượng, ví và điều kiện mint trước khi chạy.
- Chế độ tự động gửi yêu cầu lặp lại trong khoảng thời gian ngắn. API/RPC có thể giới hạn tốc độ; kết quả phụ thuộc vào OpenSea, RPC, mạng và điều kiện của drop.

## Giới hạn hiện tại

- Chỉ hỗ trợ các chain được cấu hình sẵn trong ứng dụng: Base và Robinhood Chain.
- Chỉ hoạt động với OpenSea Drops có endpoint API tương ứng; không phải mọi collection trên OpenSea đều là Drop.
- Dữ liệu phase do API trả về có thể thiếu hoặc thay đổi. Kiểm tra lại thông tin trên trang collection trước khi mint.
- Không đảm bảo mint thành công, không tự kiểm tra số dư/điều kiện whitelist trước khi gửi, và không thay thế việc tự xác minh giao dịch trên explorer.

## Đóng góp và báo lỗi

Mở **Issue** trong repository để báo lỗi hoặc đề xuất cải tiến. Không đính kèm private key, seed phrase, API key hay dữ liệu nhạy cảm.

## License

Chưa khai báo license. Hãy bổ sung file `LICENSE` trước khi cho phép người khác sử dụng, sửa đổi hoặc phân phối lại repository.
