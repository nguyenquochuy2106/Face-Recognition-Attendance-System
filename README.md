# 📸 Face Recognition Attendance System

## 📝 Giới thiệu
Hệ thống chấm công bằng nhận diện khuôn mặt cho phép nhân viên điểm danh bằng cách quét khuôn mặt thay vì sử dụng thẻ hoặc nhập mã PIN.

🔹 **Đầu vào**: Hình ảnh khuôn mặt từ camera.

🔹 **Xử lý**: Hệ thống nhận diện khuôn mặt và đối chiếu với database.

🔹 **Đầu ra**: Ghi nhận thời gian chấm công vào/ra của nhân viên.

---

## 🔄 Flow Hoạt Động
### 🏷️ **Giai đoạn đăng ký (Enrollment Phase)**

1️⃣ Nhân viên cung cấp hình ảnh khuôn mặt (chụp từ webcam hoặc upload).

2️⃣ Hệ thống thực hiện tiền xử lý ảnh, phát hiện khuôn mặt và trích xuất embedding.

3️⃣ Lưu thông tin nhân viên và embedding vào database.

### ⏳ **Giai đoạn chấm công (Recognition Phase)**
1️⃣ Nhân viên quét khuôn mặt qua camera.

2️⃣ Hệ thống phát hiện khuôn mặt và trích xuất embedding.

3️⃣ So sánh embedding với database bằng thuật toán nhận diện.

4️⃣ Nếu trùng khớp, ghi nhận thời gian vào/ra và lưu vào hệ thống.

5️⃣ Nếu không khớp, thông báo lỗi hoặc yêu cầu đăng ký.

---

## 📂 Cấu trúc thư mục
```
face_attendance/
│── backend/                    # Backend xử lý nhận diện khuôn mặt
│   ├── models/                  # Lưu mô hình đã huấn luyện
│   │   ├── facenet_model.pth     # Mô hình nhận diện khuôn mặt
│   │   ├── mtcnn.pth             # Mô hình phát hiện khuôn mặt
│   ├── database/                 # Lưu dữ liệu SQLite hoặc Firebase
│   │   ├── embeddings.db         # Lưu vector embedding của khuôn mặt
│   │   ├── attendance.db         # Lịch sử chấm công
│   │   ├── employees.db          # Lưu thông tin nhân viên
│   ├── api.py                    # API xử lý nhận diện khuôn mặt
│   ├── face_recognition.py        # Hàm nhận diện khuôn mặt
│   ├── train_model.py             # Huấn luyện mô hình nhận diện
│   ├── preprocess.py              # Tiền xử lý ảnh
│
│── frontend/                     # Giao diện Streamlit
│   ├── app.py                     # Ứng dụng chính trên Streamlit
│   ├── pages/                     # Các trang UI
│   │   ├── register.py             # Trang đăng ký nhân viên
│   │   ├── attendance.py           # Trang chấm công
│   │   ├── dashboard.py            # Trang quản lý dữ liệu
│
│── data/                         # Dữ liệu khuôn mặt
│   ├── raw_images/                # Ảnh gốc của nhân viên
│   ├── processed_images/           # Ảnh đã tiền xử lý
│
│── requirements.txt               # Các thư viện cần cài đặt
│── README.md                      # Hướng dẫn cài đặt và sử dụng
```

---

## 📜 Database
Hệ thống sử dụng **SQLite** để lưu trữ dữ liệu nhân viên và lịch sử chấm công.
- **employees.db**: Lưu thông tin nhân viên (ID, tên, email, embedding khuôn mặt).
- **embeddings.db**: Lưu vector đặc trưng của khuôn mặt nhân viên.
- **attendance.db**: Lưu lịch sử chấm công theo thời gian.

Mỗi nhân viên khi đăng ký sẽ có một embedding khuôn mặt để so sánh khi chấm công.

---

## 🚀 Công nghệ sử dụng
🔹 **Mô hình nhận diện**: CNN (FaceNet/ArcFace)  
🔹 **Backend**: FastAPI hoặc Flask  
🔹 **Database**: SQLite hoặc Firebase  
🔹 **Frontend**: Streamlit  
🔹 **Xử lý ảnh**: OpenCV, MTCNN  
🔹 **Machine Learning**: PyTorch hoặc TensorFlow  

---

## 🛠️ Cách cài đặt và chạy dự án
### 1️⃣ **Cài đặt thư viện cần thiết**
```bash
pip install -r requirements.txt
```

### 2️⃣ **Chạy Backend** (FastAPI hoặc Flask)
```bash
cd backend
python api.py
```

### 3️⃣ **Chạy ứng dụng Streamlit**
```bash
cd frontend
streamlit run app.py
```

---

## 🎯 Tính năng chính
✅ Đăng ký khuôn mặt nhân viên  
✅ Nhận diện và chấm công tự động  
✅ Lưu lịch sử chấm công vào database  
✅ Giao diện quản lý đơn giản với Streamlit  

🚀 **Sẵn sàng triển khai hệ thống chấm công thông minh!**

