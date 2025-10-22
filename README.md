# data-safe-zone_ Dataset

# 1, Dataset Các Vụ Rò Rỉ Dữ Liệu Lịch Sử cho Mô hình PRS

Đây là một bộ dữ liệu tổng hợp được tạo ra cho mục đích **nghiên cứu và xác thực Mô hình Điểm Rủi Ro Riêng Tư (Privacy Risk Score - PRS)** trong khuôn khổ **Data Safe Zone (DSZ)**.  
Dữ liệu được xây dựng dựa trên thông tin công khai về các vụ rò rỉ dữ liệu lớn và được bổ sung các trường phân tích giả lập.

---

##  Cấu trúc Dữ liệu

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

## Cách sử dụng

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
```
# 2, Historical Breach Dataset with PRS
BreachID,Entity,Year,RecordsExposed,Industry,AttackVector,SensitivityScore,VulnerabilityScore,ImpactScore,ControlEffectiveness,PrivacyRiskScore,DataAccessed
1,Yahoo,2016,3000000000,Tech,State-sponsored,8,9,10,2,360.0,"Names, email addresses, dates of birth, phone numbers, security questions"
2,Aadhaar,2018,1100000000,Government,Misconfiguration,10,8,9,3,240.0,"Names, addresses, photos, phone numbers, emails, biometric data"
3,Facebook,2021,533000000,Social Media,API Misuse,7,7,8,4,98.0,"Full names, phone numbers, locations, email addresses, relationship statuses"
4,LinkedIn,2021,700000000,Social Media,Data Scraping,6,6,8,5,57.6,"Names, email addresses, phone numbers, location, gender"
5,Marriott International,2018,500000000,Hospitality,Malware,9,8,8,3,192.0,"Names, addresses, phone numbers, email addresses, passport numbers, credit card numbers"
6,Equifax,2017,159000000,Finance,Unpatched Vulnerability,10,9,9,2,405.0,"Names, Social Security numbers, dates of birth, addresses, driver's license numbers"
7,Capital One,2019,100000000,Finance,Misconfiguration,10,7,8,4,140.0,"Names, addresses, dates of birth, income, SSNs, bank account numbers"
8,MySpace,2016,360000000,Social Media,Credential Theft,6,8,7,3,112.0,"Email addresses, usernames, and passwords"
9,Sina Weibo,2020,538000000,Social Media,Credential Theft,7,7,8,4,98.0,"Names, usernames, phone numbers, location, gender"
10,Adobe,2013,153000000,Tech,Credential Theft,8,9,8,2,288.0,"Names, email addresses, and encrypted passwords"
11,eBay,2014,145000000,E-commerce,Insider,7,8,8,3,149.33,"Names, encrypted passwords, email addresses, physical addresses, phone numbers"
12,Heartland Payment Systems,2008,130000000,Finance,Malware,10,9,9,2,405.0,"Credit and debit card numbers"
13,JPMorgan Chase,2014,76000000,Finance,Phishing,8,6,7,5,67.2,"Names, addresses, email addresses, and phone numbers"
14,Zynga,2019,218000000,Gaming,Credential Theft,7,8,7,4,98.0,"Usernames, email addresses, passwords, Facebook IDs, phone numbers"
15,Exactis,2018,340000000,Marketing,Misconfiguration,9,9,8,2,324.0,"Full names, email addresses, phone numbers, home addresses, demographic information"
16,NetEase,2015,235000000,Gaming,Credential Theft,7,8,7,3,130.67,"Usernames, passwords, and security question answers"
17,Dubsmash,2018,162000000,Social Media,API Misuse,7,7,7,4,85.75,"Usernames, email addresses, geographic locations, and passwords"
18,Alibaba,2019,1100000000,E-commerce,Insider,6,8,9,3,144.0,"User IDs and phone numbers"
19,First American Financial,2019,885000000,Finance,Misconfiguration,10,9,9,2,405.0,"SSNs, bank account details, mortgage/tax records, driver's license photos"
20,River City Media,2017,1400000000,Marketing,Misconfiguration,8,9,9,1,648.0,"Email and IP addresses, full names, and physical addresses"
