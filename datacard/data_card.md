DATA CARD — IMDB Dataset (Lab 1)
1. ASK

Người đọc:

Sinh viên NLP
ML Engineer
Researcher

Họ cần quyết định:

Dataset có đủ chất lượng để train model không?
Có cần cleaning / relabel không?

Cảnh báo cần biết:

Có duplicate (~1.6%)
Có label noise (~2%)
Có outlier text rất dài (>10k chars)
Rủi ro leakage nếu preprocessing sai thứ tự
2. Dataset Overview
Dataset: IMDB movie reviews (sentiment classification)
Số lượng: 50,000 samples
Labels: 2 lớp (0 = negative, 1 = positive)
Phân bố: cân bằng (25,000 mỗi lớp)
Split:
Train: 40,000
Val: 5,000
Test: 5,000
Text statistics:
Min length: 32
Median: 954
P95: 3328
Max: 13,593
3. Data Quality & Validation (Great Expectations)
GE result: ❌ FAIL (5/6 passed, 83.33%)
Lỗi:
len_chars vượt quá giới hạn (1–10000)
Có 6 mẫu quá dài (max = 13,593)
Tại sao nguy hiểm:
Model có thể bias theo độ dài
Training không ổn định (outlier)
Cách xử lý:
Cắt text (truncate)
Hoặc loại bỏ outliers
4. Data Auditing (Before vs After)
Vấn đề 1 — HTML artifacts
Trước: ~29,200 mẫu có <br> / HTML
Sau: 0

👉 Nguy hiểm:

Model học “shortcut” từ HTML thay vì nội dung

👉 Giải pháp:

Đã clean thành công
Vấn đề 2 — Duplicates
~832 mẫu duplicate (~1.66%)

👉 Nguy hiểm:

Data leakage
Accuracy ảo

👉 Giải pháp:

Deduplicate hoặc giữ nhưng cần cảnh báo
Vấn đề 3 — Data leakage
TF-IDF fit trên toàn bộ data (sai)

👉 Nguy hiểm:

Test set bị “lộ thông tin”

👉 Giải pháp:

Split trước → fit trên train only
5. Annotations & Labeling (Cleanlab)
Nghi vấn label lỗi: 1000 mẫu (~2%)
Review 5 mẫu (từ CSV):
ID	Nhận xét	Kết luận
11668	Review rất tích cực	Giữ nhãn
22259	Nội dung tiêu cực	Giữ nhãn
16634	Review tiêu cực rõ	Giữ nhãn
31245	Nội dung trung tính/khó	Ambiguous
32355	Có thể positive	Ambiguous

👉 Kết luận:

Có label noise nhẹ (~2%)
Không nghiêm trọng nhưng cần review nếu production
6. Transformations
Đã thực hiện:
Remove HTML tags
Chuẩn hóa text
Split train/val/test đúng
So sánh:
HTML: 29k → 0
Length: giảm nhẹ (median 970 → 954)

👉 Kết quả:

Dữ liệu sạch hơn
Giảm bias từ HTML
7. Limitations & Risks
⚠️ Hạn chế:
Vẫn còn duplicate (~1.6%)
Vẫn có HTML entity (11 mẫu)
Có outlier text dài
Có label noise (~2%)
⚠️ Rủi ro:
Model học theo độ dài
Shortcut learning
Overfitting nếu duplicate
8. Intended Use
✅ Phù hợp:
NLP sentiment classification
Research / học tập
❌ Không phù hợp:
Production nếu chưa clean kỹ
Task khác ngoài sentiment
9. Conclusion

Dataset IMDB có:

Chất lượng khá tốt
Đã clean HTML thành công
Nhưng vẫn tồn tại:
duplicates
label noise
outliers

👉 Có thể dùng cho training, nhưng cần xử lý thêm nếu dùng production.