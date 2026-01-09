# Walrus Sites Portal Runner (Testnet) On Ubuntu

Công cụ đơn giản giúp bạn nhanh chóng chạy **Walrus Sites Portal** cục bộ trên **Sui Testnet** bằng Docker.

Script sẽ tự động:
- Clone repository chính thức `MystenLabs/walrus-sites`
- Cập nhật config cho testnet
- Thiết lập **SITE_PACKAGE** (Package ID của Walrus Sites smart contract trên Sui)
- Build và chạy Docker container
Your 
Portal sẽ chạy tại: **http://localhost:3000**

Bạn có thể truy cập các site Walrus bằng **Base36 Object ID** hoặc **SuiNS testnet subdomain**.

### Yêu cầu (Prerequisites)
- **Git** — để clone repository
- **Docker** — để build và run container (Docker daemon phải đang chạy)

### Cách sử dụng (Usage)

```bash
# 1. Clone repository này
git clone https://github.com/TuanAnhDoHoang/run-site.git site-tool

# 2. Vào thư mục
cd site-tool

# 3. Cấp quyền thực thi cho script
chmod +x run-site

# 4. Chạy script với SITE_PACKAGE (bắt buộc)
./run-site <Your SITE_PACKAGE ID>
```

#### Ví dụ
```bash
./run-site 0xf99aee9f21493e1590e7e5a9aea6f343a1f381031a04a732724871fc294be799
```

> Nếu quên truyền SITE_PACKAGE, script sẽ hiển thị hướng dẫn chi tiết và thoát.

### Chạy mà không cần `./` (Tùy chọn - toàn hệ thống)
Nếu muốn chạy chỉ bằng lệnh `run-site` từ bất kỳ thư mục nào:

```bash
mkdir -p ~/bin
cp run-site ~/bin/run-site
chmod +x ~/bin/run-site

# Thêm ~/bin vào PATH (nếu chưa có)
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Sau đó:
```bash
run-site <Your SITE_PACKAGE ID>
```

### Troubleshooting
- Portal không load site → kiểm tra SITE_PACKAGE có đúng phiên bản mới nhất không.
- Xem logs container: `docker logs -f walrus-portal-server`
- Dừng container: `docker stop walrus-portal-server`
- Xóa container cũ nếu cần: `docker rm walrus-portal-server`

Enjoy your local Walrus Sites Portal on Testnet! 🚀