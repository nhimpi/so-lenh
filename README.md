# Sổ lệnh Nhím Pi

Sổ ghi giao dịch của Nhím Pi (hợp đồng tương lai VN30F1M). Repo này chỉ chứa dữ liệu để kiểm chứng sổ: không có số
tài khoản, không có dữ liệu thị trường.

## Khai sổ (GENESIS)

GENESIS được lập **trước lệnh thật đầu tiên**. Nó cố định ngày bắt đầu, vốn, giới hạn rủi ro, công thức tính và phiên
bản chiến lược, kèm một cam kết hash cho tài khoản giao dịch.

Hiện chỉ công bố **hash** của GENESIS (tệp [`GENESIS-HASH.txt`](GENESIS-HASH.txt)):

```
35f32d18151048c7d38944e0a69bf082c986963b27caaf2d85d689a1e2e5d86a
```

Nội dung đầy đủ (`genesis.json`) sẽ công bố sau. Khi đó, ai cũng tự kiểm được nội dung khớp đúng hash này: hash là
SHA-256 của tài liệu ở dạng JSON chuẩn (khoá sắp xếp, không khoảng trắng), tức toàn bộ tệp `genesis.json` trừ ký tự
xuống dòng cuối.

## Dấu thời gian

[`GENESIS-HASH.txt.ots`](GENESIS-HASH.txt.ots) là bằng chứng [OpenTimestamps](https://opentimestamps.org): hash trên đã
tồn tại trước thời điểm nó được neo vào blockchain Bitcoin. Kiểm bằng `ots verify GENESIS-HASH.txt.ots` (bằng chứng
được cập nhật sau khi giao dịch Bitcoin chứa nó được xác nhận).

## Hằng ngày

Mỗi ngày giao dịch có một manifest chỉ gồm hash và khoảng số thứ tự sự kiện của sổ, nối chuỗi về hash GENESIS. Sửa bất
kỳ sự kiện cũ nào cũng làm mọi hash phía sau sai.

## Sửa đổi luật

Luật của sổ chỉ đổi bằng một bản sửa đổi có số thứ tự và ngày hiệu lực, gắn với hash GENESIS. Hash của mỗi bản được công
bố ở đây kèm dấu OpenTimestamps, và việc nạp bản đó được ghi thành một sự kiện trong chính chuỗi sự kiện của sổ. Bản đã
nạp không sửa và không gỡ được.

- Bản số 1, hiệu lực từ 2026-11-16 (ngày đầu của sổ, nạp trước lệnh đầu tiên): [`SUA-DOI-1-HASH.txt`](SUA-DOI-1-HASH.txt),
  dấu thời gian [`SUA-DOI-1-HASH.txt.ots`](SUA-DOI-1-HASH.txt.ots).

Nội dung đầy đủ của các bản sửa đổi công bố cùng lúc với `genesis.json`; cách tính hash giống GENESIS.
