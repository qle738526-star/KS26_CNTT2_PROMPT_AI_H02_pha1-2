# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:** Lê Quốc Minh Quân
- **Lớp:**CNTT2
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt chỗ workshop ra JSON

**KET QUA AI**

```text
```json
[
  {
    "ma_lop": "NANTAY",
    "ngay_hoc": "2026-12-13",
    "tre_em": 1,
    "nguoi_lon": 2,
    "ca_hoc": "chieu",
    "ghi_chu": null
  },
  {
    "ma_lop": "BANXOAY",
    "ngay_hoc": "2027-01-10",
    "tre_em": 0,
    "nguoi_lon": 3,
    "ca_hoc": null,
    "ghi_chu": "Một người bị đau cổ tay"
  },
  {
    "ma_lop": "VEGOM",
    "ngay_hoc": null,
    "tre_em": 0,
    "nguoi_lon": 4,
    "ca_hoc": "sang",
    "ghi_chu": "Một bạn đi xe lăn"
  }
]

``````

**Link trò chuyện:**https://share.gemini.google/ezu29i63mv5Y

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
```python
price_adult = 550000
adults = 5
cost_adults = adults * price_adult

# Children: 8 yo (6-12 -> 70%), 12 yo (6-12 -> 70%), 4 yo (<6 -> free)
price_child_6_12 = 0.7 * price_adult
cost_child_8 = price_child_6_12
cost_child_12 = price_child_6_12
cost_child_4 = 0
cost_children = cost_child_8 + cost_child_12 + cost_child_4

tuition_before_discount = cost_adults + cost_children

# Group >= 5 adults -> 5% discount on tuition
discount = 0.05 * tuition_before_discount if adults >= 5 else 0
tuition_after_discount = tuition_before_discount - discount

# Firing and delivery: 4 items * 80,000
items = 4
fee_per_item = 80000
shipping_fee = items * fee_per_item

total = tuition_after_discount + shipping_fee

print(f"cost_adults: {cost_adults:,.0f}")
print(f"price_child_6_12: {price_child_6_12:,.0f}")
print(f"cost_children: {cost_children:,.0f}")
print(f"tuition_before_discount: {tuition_before_discount:,.0f}")
print(f"discount: {discount:,.0f}")
print(f"tuition_after_discount: {tuition_after_discount:,.0f}")
print(f"shipping_fee: {shipping_fee:,.0f}")
print(f"total: {total:,.0f}")


```

```text
cost_adults: 2,750,000
price_child_6_12: 385,000
cost_children: 770,000
tuition_before_discount: 3,520,000
discount: 176,000
tuition_after_discount: 3,344,000
shipping_fee: 320,000
total: 3,664,000


```

Dưới đây là chi tiết tính toán báo giá cho lớp **BANXOAY** (đơn giá: 550.000 đồng/người lớn) theo từng bước:

**Bước 1: Tính tiền người lớn**

* Nhóm có 5 người lớn: $5 \times 550.000 = 2.750.000\text{ đồng}$

**Bước 2: Tính tiền trẻ em (tính theo từng độ tuổi)**

* Bé 8 tuổi (thuộc nhóm 6–12 tuổi, tính 70% giá người lớn): $550.000 \times 70\% = 385.000\text{ đồng}$
* Bé 12 tuổi (thuộc nhóm 6–12 tuổi, tính 70% giá người lớn): $550.000 \times 70\% = 385.000\text{ đồng}$
* Bé 4 tuổi (dưới 6 tuổi đi kèm, miễn phí): $0\text{ đồng}$
* Tổng tiền trẻ em: $385.000 + 385.000 + 0 = 770.000\text{ đồng}$

**Bước 3: Tiền học (tiền trẻ em cộng tiền người lớn)**

* Tiền học trước giảm giá: $770.000 + 2.750.000 = 3.520.000\text{ đồng}$

**Bước 4: Giảm giá nhóm (tính theo điều kiện, tiền sau khi giảm)**

* Điều kiện: Nhóm có 5 người lớn (đạt mức từ 5 người lớn trở lên) nên được giảm 5% trên tổng tiền học.
* Số tiền được giảm: $3.520.000 \times 5\% = 176.000\text{ đồng}$
* Tiền học sau khi giảm: $3.520.000 - 176.000 = 3.344.000\text{ đồng}$

**Bước 5: Phí nung và giao**

* Nhóm cần nung và giao 4 sản phẩm (không áp dụng giảm giá): $4 \times 80.000 = 320.000\text{ đồng}$

**Bước 6: Tổng tiền**

* Tổng số tiền thanh toán: $3.344.000 + 320.000 = 3.664.000\text{ đồng}$

**Kiểm tra & Kết luận:** **Đúng.** Tất cả các bước từ Bước 1 đến Bước 6 đều đã đối chiếu chính xác với đơn giá lớp BANXOAY, tỷ lệ tính giá theo từng độ tuổi, điều kiện chiết khấu 5% cho nhóm từ 5 người lớn và quy tắc không giảm giá đối với phí nung/giao hàng.

[RESULT:3.664.000 đồng]```

**Link trò chuyện:**https://share.gemini.google/UJ5zxQY3xduy

### b) Kiểm tra kết quả AI

**Kết luận: Đúng.**

Toàn bộ 6 bước tính toán và con số tổng cuối cùng (**3.664.000 đồng**) ở câu trả lời trước đều khớp chính xác với dữ liệu bảng giá và các quy tắc áp dụng.

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
### Trạm 1: Trích xuất dữ liệu JSON

```json
{
  "loai_su_co": "hong_san_pham",
  "so_khach": 3,
  "so_san_pham_bi_hong": 5,
  "tom_tat": "Gia đình 3 người tham gia lớp nặn gốm ngày 01/11/2026 làm tổng cộng 6 sản phẩm, khi nhận hàng có 5 sản phẩm bị nứt vỡ."
}

```

---

### Phân tích số liệu và Giải thích phương án xử lý

* **Phân loại sự cố (`hong_san_pham`):** Khách hàng phản ánh có 5 sản phẩm bị nứt vỡ khi nhận hàng. Khách hàng khen ngợi người hướng dẫn nhiệt tình và không đề cập đến việc giao trễ, do đó loại trừ các trường hợp `huong_dan`, `giao_tre` và `khac`.
* **Số lượng khách (`3`):** Dữ liệu ghi nhận "Gia đình tôi 3 người". (Thông tin này được lưu trữ để đối chiếu hồ sơ, không dùng để nhân đơn giá đền bù cho loại sự cố hỏng sản phẩm).
* **Số lượng sản phẩm và tỷ lệ hư hỏng (`5/6` sản phẩm):** Mỗi người làm 2 sản phẩm, tương đương tổng cộng $3 \times 2 = 6$ sản phẩm. Trong đó có 5 sản phẩm bị nứt vỡ.
* **Tính toán mức đền bù:**
* Theo chính sách đối với lỗi `hong_san_pham`, mức hoàn tiền là **150.000 đồng / sản phẩm bị hỏng**.
* Tổng tiền hoàn lại cho khách hàng: $5 \times 150.000 = \mathbf{750.000\text{ đồng}}$.


* **Quy trình phê duyệt:**
* Vì tổng mức đền bù là **750.000 đồng** (vượt quá hạn mức 600.000 đồng theo quy định), chuyên viên cần **trình Quản lý xưởng phê duyệt** trước khi gửi phản hồi và tiến hành hoàn tiền cho khách hàng.
```

**Link trò chuyện:**https://share.gemini.google/JmI8mYdKRdxl

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
| Tiêu chí | Điểm | Đề xuất sửa (Câu bị lỗi - Lý do sai - Câu sửa đề xuất) |
| --- | --- | --- |
| **Đúng thông tin (50%)** | 0 / 5.0 | **Lỗi 1:**<br>

<br>- **Câu bị lỗi:** "Lớp vẽ gốm bên em 200k thôi nè..."<br>

<br>- **Lý do sai:** Báo sai giá so với thông tin chuẩn của công ty (250.000 đồng/người lớn).<br>

<br>- **Câu sửa đề xuất:** "Dạ, lớp vẽ gốm bên em có giá là 250.000 đồng/người lớn ạ."<br>

<br>

<br>**Lỗi 2:**<br>

<br>- **Câu bị lỗi:** "Chị đổi trước 1 ngày thì free nha chị."<br>

<br>- **Lý do sai:** Sai chính sách đổi lịch. Đổi trước 1 ngày (24 giờ) thuộc khung từ 12 đến dưới 48 giờ, mất phí 30.000 đồng/người (chỉ miễn phí khi đổi trước từ 48 giờ trở lên).<br>

<br>- **Câu sửa đề xuất:** "Nếu chị đổi lịch trước giờ học 1 ngày (24 giờ), phí đổi lịch sẽ là 30.000 đồng/người ạ (bên em chỉ miễn phí khi đổi trước từ 48 giờ trở lên)." |
| **Đầy đủ (30%)** | 1.5 / 3.0 | **Lỗi:**<br>

<br>- **Câu bị lỗi:** "Có gì chị nhắn em nha!"<br>

<br>- **Lý do sai:** Đã trả lời đủ 2 ý hỏi của khách nhưng thiếu lời mời khách cung cấp thông tin (ngày học, ca học, số lượng người) để tiến hành đặt chỗ.<br>

<br>- **Câu sửa đề xuất:** "Chị vui lòng cho em xin thông tin về ngày học, ca học và số lượng người tham gia để em hỗ trợ đặt chỗ cho mình nhé!" |
| **Giọng điệu (20%)** | 0.5 / 2.0 | **Lỗi:**<br>

<br>- **Câu bị lỗi:** "Hi chị ơi!", "...200k thôi nè, vui lắm luôn.", "...free nha chị. Có gì chị nhắn em nha!"<br>

<br>- **Lý do sai:** Sử dụng nhiều từ ngữ suồng sã, thiếu tính chuyên nghiệp ("hi", "nè", "vui lắm luôn", "free", "nha").<br>

<br>- **Câu sửa đề xuất:** "Dạ chào chị ạ! Lớp vẽ gốm bên em có mức giá là 250.000 đồng/người lớn. Nếu chị đổi sang buổi khác trước giờ học 1 ngày (24 giờ), phí đổi lịch sẽ là 30.000 đồng/người ạ. Chị vui lòng cung cấp giúp em ngày học, ca học và số người tham gia để em hỗ trợ đặt chỗ cho chị nhé!" |
| **Tổng điểm** | **2.0 / 10** |  |
```

**Link trò chuyện:**https://share.gemini.google/F530herkkxrT
