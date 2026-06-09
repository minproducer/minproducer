# HƯỚNG DẪN SỬ DỤNG HỆ THỐNG TỰ ĐỘNG ĐĂNG BÀI FACEBOOK GROUP

## 1. Tổng quan hệ thống

Hệ thống giúp:

* Tự động tạo bài viết tuyển dụng bằng AI từ JD.
* Tự động chọn nhóm Facebook phù hợp.
* Tự động load ảnh từ Google Drive.
* Tự động đăng vào tối đa 3 nhóm Facebook cho mỗi bài.
* Theo dõi link bài đăng và trạng thái đăng bài.

Quy trình hoạt động:

**JD → AI viết bài → Duyệt → Chọn group → Load ảnh → Đăng bài → Lưu link bài viết**

---

# 2. Quy trình sử dụng

## BƯỚC 1 — Điền JD tuyển dụng

Mở Sheet:

**Form JD**

Điền đầy đủ thông tin tuyển dụng:

### Các trường nên có

* Vị trí tuyển dụng
* Thu nhập
* Địa điểm làm việc
* Hình thức và thời gian làm việc
* Mô tả công việc
* Yêu cầu
* Quyền lợi
* Email nhà tuyển dụng
* Website / số điện thoại (nếu có)

### Lưu ý

* Càng đầy đủ → AI viết càng hay.
* Không cần format đẹp.
* Có thể copy JD thô.

Ví dụ:

**Vị trí tuyển dụng**

Telesale giáo dục

**Thu nhập**

13–35 triệu

**Quyền lợi**

* Data nóng
* Lương cứng
* Hoa hồng
* Review lương hàng tháng

---

## BƯỚC 2 — AI tự tạo content

Hệ thống sẽ:

* Đọc JD
* Tự viết bài tuyển dụng hấp dẫn
* Tự tối ưu để tăng ứng tuyển

Kết quả sẽ xuất hiện trong sheet:

**content AI**

---

## BƯỚC 3 — Kiểm tra nội dung AI

Mở sheet:

**content AI**

Kiểm tra:

### Nội dung

AI viết bài.

### Chỉnh sửa (nếu muốn)

Có thể sửa trực tiếp.

### Link folder ảnh Drive

Paste link thư mục ảnh tương ứng với bài viết.

Ví dụ:

https://drive.google.com/drive/folders/xxxxxxxxx

### Đã phê duyệt

Đổi thành:

```txt
true
```

nếu muốn đăng.

Nếu để:

```txt
false
```

→ hệ thống sẽ bỏ qua.

---

## BƯỚC 4 — Chuẩn bị ảnh bài đăng

Tạo folder Google Drive chứa ảnh.

Ví dụ:

* ảnh 1
* ảnh 2
* ảnh 3

Sau đó copy link folder:

Ví dụ:

https://drive.google.com/drive/folders/1RZROaI5v0Bst2xxkznydHdMXl-66U1Dq

Paste vào cột:

**Link folder ảnh Drive**

### Lưu ý quan trọng

Folder phải:

**Bật chia sẻ Anyone with link**

Nếu không Facebook sẽ không tải được ảnh.

---

## BƯỚC 5 — Danh sách nhóm Facebook

Hệ thống có sheet riêng quản lý group.

Điền:

### Tên nhóm Sales

Tên nhóm.

### Link Real

Link group Facebook thật.

Ví dụ:

https://www.facebook.com/groups/123456789

Hệ thống tự:

* đồng bộ group vào database
* đánh giá
* chọn nhóm
* tránh đăng lặp

---

## BƯỚC 6 — Tự động đăng bài

Khi content:

```txt
Đã phê duyệt = true
Đã đăng = false
```

hệ thống sẽ:

1. Chọn tối đa 3 group.
2. Load ảnh từ Drive.
3. Upload ảnh.
4. Đăng vào từng group.
5. Ghi lại link bài viết.
6. Đánh dấu đã đăng.

---

# 3. Ý nghĩa các cột trong sheet

## Đã phê duyệt

```txt
true
```

→ cho phép đăng

```txt
false
```

→ không đăng

---

## Đã đăng

```txt
true
```

→ đã đăng xong

```txt
false
```

→ chưa đăng

---

## ID Nhóm

Danh sách group đã được hệ thống chọn.

Ví dụ:

```txt
415428978792627,182139539952245,1330629366955900
```

---

## Link bài viết

Link bài đã đăng.

Ví dụ:

Group 1/3 (415428978792627): https://facebook.com/xxxxx

Group 2/3 (182139539952245): https://facebook.com/yyyyy

Group 3/3 (1330629366955900): https://facebook.com/zzzzz

---

## Thời gian đăng

Thời điểm hệ thống bắt đầu đăng.

---

# 4. Các lỗi thường gặp

## Không đăng được ảnh

Nguyên nhân:

Folder Drive chưa public.

Cách sửa:

Bật:

**Anyone with link → Viewer**

---

## Không có group

Nguyên nhân:

Sheet group chưa có dữ liệu.

Cách sửa:

Thêm group vào sheet group.

---

## Không đăng bài

Kiểm tra:

```txt
Đã phê duyệt = true
Đã đăng = false
```

---

## Không có ảnh

Kiểm tra:

Cột:

**Link folder ảnh Drive**

đã đúng link chưa.

---

## Facebook đăng thiếu ảnh

Nguyên nhân thường gặp:

Ảnh trong Drive chưa public hoặc Facebook lỗi upload.

Giải pháp:

Chạy lại workflow.

---

# 5. Quy tắc sử dụng

### Không sửa cột hệ thống

Không sửa:

* ID Nhóm
* Link bài viết
* Thời gian đăng
* Đã đăng thành công

---

### Có thể sửa

Được sửa:

* Nội dung
* Link folder ảnh Drive
* Đã phê duyệt

---

### Một content đăng tối đa bao nhiêu group?

Mặc định:

**3 group / lần chạy**

Có thể chỉnh tăng giảm theo nhu cầu.

---

### Có bị đăng trùng group không?

Không.

Hệ thống có cơ chế:

* nhớ lịch sử
* xoay vòng group
* reset khi dùng hết group

---

### Có thể đăng lại bài cũ không?

Có.

Đổi:

```txt
Đã đăng = false
```

rồi chạy lại.
