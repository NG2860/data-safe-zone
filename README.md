# data-safe-zone_ Dataset

# 1, Dataset Các Vụ Rò Rỉ Dữ Liệu Lịch Sử cho Mô hình PRS

Đây là một bộ dữ liệu tổng hợp được tạo ra cho mục đích **nghiên cứu và xác thực Mô hình Điểm Rủi Ro Riêng Tư (Privacy Risk Score - PRS)** trong khuôn khổ **Data Safe Zone (DSZ)**.  
Dữ liệu được xây dựng dựa trên thông tin công khai về các vụ rò rỉ dữ liệu lớn và được bổ sung các trường phân tích giả lập.

---

## 📁 Cấu trúc Dữ liệu

Tệp `historical_breach_dataset.csv` chứa các cột sau:

| Tên cột              | Kiểu dữ liệu | Mô tả                                                                                   | Thang đo |
|----------------------|--------------|-----------------------------------------------------------------------------------------|----------|
| BreachID             | Integer      | Mã định danh duy nhất cho mỗi vụ rò rỉ.                                                | -        |
| Entity               | String       | Tên của tổ chức/nền tảng bị rò rỉ.                                                    | -        |
| Year                 | Integer      | Năm xảy ra vụ rò rỉ (hoặc được phát hiện).                                            | -        |
| RecordsExposed       | Integer      | Số lượng hồ sơ ước tính bị ảnh hưởng.                                                 | -        |
| Industry             | String       | Lĩnh vực hoạt động của tổ chức (ví dụ: Social Media, Finance, Government).           | -        |
| AttackVector         | String       | Vector tấn công chính gây ra sự cố (ví dụ: API Misuse, Phishing, Insider).            | -        |
| SensitivityScore     | Integer      | (S) - Điểm số đánh giá mức độ nhạy cảm của dữ liệu bị lộ.                              | 1-10     |
| VulnerabilityScore   | Integer      | (V) - Điểm số đánh giá lỗ hổng của nền tảng/quy trình.                                | 1-10     |
| ImpactScore          | Integer      | (I) - Điểm số đánh giá tác động tiềm tàng của vụ rò rỉ.                               | 1-10     |
| ControlEffectiveness | Integer      | (C) - Điểm số đánh giá hiệu quả của các biện pháp kiểm soát tại thời điểm đó.         | 1-10     |
| PrivacyRiskScore     | Float        | (PRS) - Điểm rủi ro được tính toán theo công thức: (S * V * I) / C.                  | -        |
| DataAccessed         | String       | Mô tả chi tiết các loại dữ liệu đã bị truy cập.                                       | -        |

---

## 📝 Ghi chú

Các điểm số **SensitivityScore**, **VulnerabilityScore**, **ImpactScore**, và **ControlEffectiveness** là các giá trị **giả lập** được tạo ra dựa trên phân tích định tính các báo cáo công khai để phục vụ cho việc xác thực mô hình.  

Bộ dữ liệu này **không nhằm mục đích phản ánh chính xác tuyệt đối** mọi chi tiết của các sự cố, mà là một **công cụ nghiên cứu** để kiểm tra và chứng minh tính hợp lệ của mô hình **PRS**.

---

## 🚀 Cách sử dụng

Bạn có thể sử dụng bộ dữ liệu này với script Python trong repository  
**`Privacy-Risk-Score-Model`** để tái tạo lại các phân tích và biểu đồ.

Ví dụ:

```python
import pandas as pd

# Đọc dữ liệu
df = pd.read_csv("historical_breach_dataset.csv")

# Xem 5 dòng đầu tiên
print(df.head())

# Tính điểm PRS trung bình
print(df["PrivacyRiskScore"].mean())


