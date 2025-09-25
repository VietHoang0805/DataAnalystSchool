# 🎤 Script thuyết trình: Tiền xử lý dữ liệu  

---

## Slide 1 – Tiêu đề  
Xin chào mọi người, hôm nay mình sẽ trình bày **Chương 3: Tiền xử lý dữ liệu**,  
áp dụng trên bộ dataset *Marketing Campaign Performance* từ Kaggle.  
Đây là một bước cực kỳ quan trọng trước khi phân tích và xây dựng mô hình.  

---

## Slide 2 – Mục tiêu  
Mục tiêu của bài hôm nay:  
1. Hiểu khái niệm và ý nghĩa tiền xử lý dữ liệu.  
2. Thực hành các bước cơ bản trên dataset thực tế.  
3. Đi qua 5 nhóm thao tác chính:  
   - Làm sạch  
   - Chuẩn hóa  
   - Xử lý dữ liệu thiếu  
   - Xử lý ngoại lai  
   - Biến đổi nâng cao  

---

## Slide 3 – 1. Làm sạch dữ liệu  
- **Xóa biến không cần thiết**  
  - Ví dụ: *Customer_ID* chỉ là định danh, không giúp phân tích ROI/CTR → xóa để dữ liệu gọn.  

- **Tạo biến mới có giá trị**  
  - Ví dụ: ROI = Revenue / Spend → đánh giá hiệu quả đầu tư.  
  - Ngoài ra: Margin %, CTR, CPC, Conversion Rate, Age_Group.  

👉 Mục tiêu: dữ liệu tập trung hơn, giàu insight hơn.  

---

## Slide 4 – 2. Chuẩn hóa dữ liệu  
- **Định nghĩa:** đưa dữ liệu về cùng thang đo.  
- **Ý nghĩa:** tránh biến lớn (Impressions) lấn át biến nhỏ (Clicks).  
- **Khi cần:** trực quan hóa, KNN, SVM, PCA.  
- **Khi không cần:** giữ giá trị gốc để giải thích thực tế, hoặc dùng tree-based models.  

👉 Ví dụ: chuẩn hóa *Impressions* và *Clicks* bằng Min-Max (0–1) hoặc Z-score.  

---

## Slide 5 – 3. Xử lý dữ liệu thiếu  
- **Định nghĩa:** giá trị trống hoặc NaN.  
- **Kiểm tra:** `isnull().sum()`.  
- **Option xử lý:**  
  1. Xóa dòng/cột nếu thiếu ít hoặc toàn bộ trống.  
  2. Thay bằng trung bình/median/mode.  
  3. Thay theo nhóm (ví dụ tuổi TB theo kênh).  
  4. Gán giá trị đặc biệt (Unknown, -1) → giữ như một nhóm riêng.  

👉 Ví dụ: cột Age bị thiếu → có thể xóa, thay trung bình, hoặc gán Unknown để phân tích riêng.  

---

## Slide 6 – 4. Xử lý dữ liệu ngoại lai  
- **Mục đích:** tránh méo kết quả phân tích và trực quan hóa.  
- **Khi nên loại bỏ:** chắc chắn lỗi nhập, hoặc chỉ quan tâm xu hướng chung.  
- **Khi không nên loại bỏ:** ngoại lai phản ánh chiến dịch lớn thật sự, hoặc khi muốn tìm điểm đặc biệt.  

**Option xử lý:**  
1. Xóa dòng ngoại lai.  
2. Cắt ngưỡng (winsorization).  
3. Log transform để giảm ảnh hưởng.  
4. Tạo cột `is_outlier` để mô hình học phân biệt.  

👉 Ví dụ: Spend = 100,000 → có thể xóa, cắt max=5000, lấy log, hoặc giữ lại nhưng đánh dấu.  

---

## Slide 7 – 5. Biến đổi dữ liệu nâng cao  
### Với **Text**  
- Chuẩn hóa chữ hoa/thường.  
- Loại bỏ ký tự, stopwords.  
- TF-IDF, Bag-of-Words.  
👉 Mục tiêu: gom nhóm, phân tích nội dung chiến dịch.  

### Với **Time**  
- Tách ngày, tháng, quý, mùa.  
- Tính thời lượng chiến dịch, khoảng cách giữa các chiến dịch.  
- Đánh dấu cuối tuần, ngày lễ.  
👉 Mục tiêu: phân tích xu hướng theo thời gian.  

### Ngoài ra còn có  
1. Biến đổi phân phối (log, Box-Cox).  
2. Mã hóa dữ liệu phân loại (one-hot, target encoding).  
3. Tạo biến tương tác (Spend × Season).  
4. Giảm chiều dữ liệu (PCA, Autoencoder).  
5. Biến đổi theo miền (LTV, RFM trong marketing).  
6. Theo nhóm (chuẩn hóa trong từng kênh).  

👉 Mục tiêu: làm dữ liệu giàu ý nghĩa, sẵn sàng cho phân tích và mô hình.  

---

## Slide 8 – Kết luận  
- Tiền xử lý dữ liệu là **nền tảng**.  
- Làm sạch → dữ liệu gọn & giàu thông tin.  
- Chuẩn hóa, xử lý thiếu & ngoại lai → dữ liệu đồng nhất, đáng tin cậy.  
- Biến đổi nâng cao → khai thác insight sâu hơn.  

👉 Sau xử lý, dataset Marketing Campaign Performance có thể dùng để phân tích ROI, CTR, hoặc dự đoán hiệu quả chiến dịch.  
