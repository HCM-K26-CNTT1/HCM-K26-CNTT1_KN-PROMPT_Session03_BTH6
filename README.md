# **BÀI THỰC HÀNH 6: CHUẨN HÓA DỮ LIỆU SINH VIÊN THÀNH JSON**

## **PHẦN 1. XÂY DỰNG PROMPT THEO CREATE**

### **1.1. Prompt CREATE hoàn chỉnh**

```
[C - Context]
Bạn là chuyên viên quản lý dữ liệu của Phòng Đào tạo, có nhiệm vụ kiểm tra và chuẩn hóa thông tin sinh viên trước khi đưa vào hệ thống quản lý.

[R - Request]
Hãy đọc dữ liệu đầu vào, chuẩn hóa thông tin sinh viên và chuyển đổi thành định dạng JSON theo cấu trúc được yêu cầu.

[E - Explanation]
Các quy tắc bắt buộc:
- fullName: Lưu họ và tên đầy đủ của sinh viên.
- email: Lưu địa chỉ email tương ứng.
- status: Chỉ được nhận một trong ba giá trị:
  + đang học
  + bảo lưu
  + nghỉ học
- Không tự ý bổ sung hoặc suy đoán thông tin.
- Không được làm mất hoặc gộp bất kỳ bản ghi nào.
- Nếu trường dữ liệu không xác định được, sử dụng giá trị "UNKNOWN".
- Giữ nguyên chính xác thông tin họ tên và email từ dữ liệu đầu vào.
- JSON phải đúng cú pháp và hợp lệ.

[A - Action]
Thực hiện lần lượt các bước:
1. Đọc toàn bộ dữ liệu đầu vào.
2. Tách từng bản ghi thành họ tên, email và trạng thái.
3. Chuẩn hóa trạng thái theo ba giá trị đã quy định.
4. Chuyển từng bản ghi thành một đối tượng JSON.
5. Đếm tổng số bản ghi đầu vào.
6. Kiểm tra số lượng bản ghi JSON đầu ra phải bằng số lượng bản ghi đầu vào.
7. Kiểm tra các trường dữ liệu và tính hợp lệ của JSON trước khi xuất kết quả.

Dữ liệu đầu vào:
Nguyễn Văn An - an.nguyen@gmail.com - đang học
Trần Thị Bình - binhtt@gmail.com - bảo lưu
Lê Hoàng Nam - nam.le@gmail.com - đang học
Phạm Minh Đức - duc.pham@gmail.com - nghỉ học

[T - Tone]
Sử dụng cách xử lý chính xác, khách quan, nhất quán. Không thêm nhận xét hoặc thông tin không có trong dữ liệu.

[E - Extras]
- Chỉ trả về JSON thô.
- Không sử dụng Markdown Code Fence.
- Không giải thích bên ngoài JSON.
- Sử dụng cấu trúc:
{
  "students": [
    {
      "fullName": "Họ và tên",
      "email": "Email",
      "status": "Trạng thái"
    }
  ],
  "totalRecords": 4
}
- Đảm bảo JSON hợp lệ và totalRecords khớp với số lượng sinh viên thực tế.
```

## **PHẦN 2. KẾT QUẢ SAU KHI SỬ DỤNG PROMPT**

### **2.1. Kết quả JSON**

```

{
  "students": [
    {
      "fullName": "Nguyễn Văn An",
      "email": "an.nguyen@gmail.com",
      "status": "đang học"
    },
    {
      "fullName": "Trần Thị Bình",
      "email": "binhtt@gmail.com",
      "status": "bảo lưu"
    },
    {
      "fullName": "Lê Hoàng Nam",
      "email": "nam.le@gmail.com",
      "status": "đang học"
    },
    {
      "fullName": "Phạm Minh Đức",
      "email": "duc.pham@gmail.com",
      "status": "nghỉ học"
    }
  ],
  "totalRecords": 4
}

```

## **PHẦN 3. KIỂM TRA VÀ ĐÁNH GIÁ KẾT QUẢ**

### **3.1. Kiểm tra dữ liệu**

| Tiêu chí kiểm tra        | Kết quả |
| ------------------------ | ------- |
| Số bản ghi đầu vào       | 4       |
| Số bản ghi đầu ra        | 4       |
| Đầy đủ họ tên            | Đạt     |
| Đầy đủ email             | Đạt     |
| Trạng thái đúng quy định | Đạt     |
| Không mất bản ghi        | Đạt     |
| totalRecords chính xác   | Đạt     |
| Cấu trúc JSON hợp lệ     | Đạt     |

### **3.2. Kiểm tra cú pháp JSON**

Sử dụng công cụ [JSONLint](https://jsonlint.com/?utm_source=chatgpt.com) để kiểm tra tính hợp lệ của JSON.

Các bước thực hiện:

1. Sao chép nội dung JSON ở Phần 2.
2. Truy cập trang JSONLint.
3. Dán nội dung JSON vào khung kiểm tra.
4. Nhấn Validate JSON.
5. Kiểm tra kết quả thông báo hợp lệ (Valid JSON).
