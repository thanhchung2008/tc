# BÀI LÀM PHA 2 (ĐỀ LUYỆN TẬP CHỦ ĐỀ CHẠY AFFILIATE)

- **Họ tên:**
- **Lớp:**
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đăng ký gói Affiliate ra JSON

**KET QUA AI**

```text
[
  {
    "ma_goi": "TT",
    "ngay_bat_dau": "2026-12-20",
    "creator_chinh": 2,
    "thuc_tap_sinh": 1,
    "hang_tai_khoan": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": "SP",
    "ngay_bat_dau": "2027-01-08",
    "creator_chinh": 3,
    "thuc_tap_sinh": 0,
    "hang_tai_khoan": null,
    "ghi_chu": "ngồi bàn gần cửa ra vào"
  },
  {
    "ma_goi": "PRO",
    "ngay_bat_dau": null,
    "creator_chinh": 4,
    "thuc_tap_sinh": 0,
    "hang_tai_khoan": "vip",
    "ghi_chu": "mượn thêm đèn trợ sáng và phông xanh để quay mẫu"
  }
]
```

**Link trò chuyện:**https://share.gemini.google/Gn28UY2YY15r

## 4.3. Báo giá gói Affiliate bằng Chain-of-Thought

**KET QUA AI**

```text
```python
creator_price = 1_500_000
num_creators = 4
creator_total = num_creators * creator_price

intern_unit_price = int(creator_price * 0.60) # 900,000
num_interns = 2 # 16 and 17 years old (15 to under 18)
intern_total = num_interns * intern_unit_price # 1,800,000
# 7-year-old child is free (0)

package_total = creator_total + intern_total # 6,000,000 + 1,800,000 = 7,800,000

# Team >= 4 creators -> 10% discount on package_total
discount = int(package_total * 0.10) # 780,000
after_discount = package_total - discount # 7,020,000

# 2 wireless mic sets * 250,000
mic_total = 2 * 250_000 # 500,000

grand_total = after_discount + mic_total # 7,520,000

print(f"creator_total: {creator_total:,}")
print(f"intern_unit_price: {intern_unit_price:,}, intern_total: {intern_total:,}")
print(f"package_total: {package_total:,}")
print(f"discount: {discount:,}, after_discount: {after_discount:,}")
print(f"mic_total: {mic_total:,}")
print(f"grand_total: {grand_total:,}")


```

```text
creator_total: 6,000,000
intern_unit_price: 900,000, intern_total: 1,800,000
package_total: 7,800,000
discount: 780,000, after_discount: 7,020,000
mic_total: 500,000
grand_total: 7,520,000


```

* Tiền Creator chính: 4 × 1.500.000 = 6.000.000 đồng
* Tiền thực tập sinh: 2 thực tập sinh (16 tuổi và 17 tuổi, thuộc nhóm từ 15 đến dưới 18 tuổi, mỗi người tính 60% của 1.500.000 = 900.000 đồng; bé 7 tuổi dưới 15 tuổi ngồi khu chờ được miễn phí = 0 đồng): 2 × (1.500.000 × 60%) = 2 × 900.000 = 1.800.000 đồng
* Tổng tiền gói: 6.000.000 + 1.800.000 = 7.800.000 đồng
* Giảm giá team: Team có 4 Creator chính (từ 4 Creator chính trở lên), giảm 10% trên tổng tiền gói: 7.800.000 × 10% = 780.000 đồng (tiền gói sau giảm: 7.800.000 - 780.000 = 7.020.000 đồng)
* Phụ thu thuê mic: 2 × 250.000 = 500.000 đồng
* Tổng tiền: 7.020.000 + 500.000 = 7.520.000 đồng
[RESULT: 7.520.000 đồng]
```

**Link trò chuyện:**https://share.gemini.google/2aij3IHaDnpR

### b) Kiểm tra kết quả AI

AI làm đúng

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "sai_phong",
  "so_khach": 3,
  "so_ca_bi_anh_huong": 2,
  "tom_tat": "Bị xếp sai phòng thiếu đèn livestream và cách âm trong 2 ca thực chiến đầu tiên."
}
```

**Link trò chuyện:**https://share.gemini.google/vjxtIvuADrEc

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Minh chứng | Đề xuất sửa |
| --- | --- | --- | --- |
| Đúng thông tin | 0/5,0 | - Nguyên văn: *"Gói TikTok Affiliate bên mình giá chỉ 1.200.000đ/người thôi"* -> Sai giá gói chuẩn (1.500.000 đồng/Creator chính).<br>

<br>- Nguyên văn: *"Bạn báo huỷ trước 5 ngày thì được hoàn lại đủ 100% tiền nha"* -> Sai chính sách hoàn tiền; huỷ trước 5 ngày (nằm trong khoảng từ 3 đến 6 ngày) chỉ được hoàn 50%, hoàn 100% áp dụng khi huỷ trước từ 7 ngày trở lên. | - *"Gói TikTok Affiliate (TT) đợt này có mức phí là 1.500.000 đồng/Creator chính ạ."*<br>

<br>- *"Trường hợp anh/chị báo huỷ trước ngày bắt đầu 5 ngày (thuộc khung từ 3 đến 6 ngày trước ngày bắt đầu), trung tâm sẽ hỗ trợ hoàn lại 50% học phí ạ. Chính sách hoàn 100% chỉ áp dụng khi báo huỷ trước từ 7 ngày trở lên, còn dưới 3 ngày sẽ không hoàn tiền ạ."* |
| Đầy đủ | 1,5/3,0 | - Trả lời được 2 câu hỏi của khách hàng (giá gói và trường hợp huỷ trước 5 ngày).<br>

<br>- Thiếu nội dung mời khách hàng cung cấp ngày đợt thực chiến và số lượng suất muốn đăng ký. | - *"Để em hỗ trợ giữ chỗ chính xác, anh/chị cho em xin thông tin ngày đợt thực chiến anh/chị dự kiến tham gia và số lượng suất muốn đăng ký nhé."* |
| Giọng điệu | 0/2,0 | - Nguyên văn: *"Dạ hello bạn nha!"*, *"...nha, cứ chốt lẹ kẻo hết slot nè!"* -> Dùng từ ngữ suồng sã, thiếu chuyên nghiệp (*hello, nha, chốt lẹ, nè*).<br>

<br>- Nguyên văn: *"...đăng ký xong gắn link là nổ đơn hoa hồng trăm triệu luôn ạ."* -> Cam kết doanh thu/hoa hồng ảo, không có cơ sở. | - *"Dạ em chào anh/chị ạ. Hiệu quả kinh doanh và mức hoa hồng thực tế phụ thuộc vào năng lực triển khai, sản phẩm và nội dung của từng kênh, trung tâm không cam kết mức doanh thu cố định ạ. Anh/chị cân nhắc đăng ký sớm để chủ động sắp xếp lịch tham gia đợt học ạ."* |

Tổng điểm: 1,5/10
```

**Link trò chuyện:**https://share.gemini.google/Sg6vDMk4wc48
