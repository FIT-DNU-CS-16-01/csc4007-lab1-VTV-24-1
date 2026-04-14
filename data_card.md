# DATA CARD — IMDB Dataset

---

## 🔹 3 Câu hỏi nền tảng

**Ai sẽ đọc Data Card?**  
- Sinh viên NLP, ML Engineer, Data Scientist, Researcher  

**Họ cần quyết định gì?**  
- Dataset có đủ chất lượng để train model không  
- Có cần cleaning hoặc xử lý thêm không  

**Họ cần cảnh báo gì?**  
- Dataset có duplicate (~1.66%)  
- Có label noise (~2%)  
- Có outliers (text dài >10000)  
- Rủi ro leakage nếu xử lý sai pipeline  

---

# 🔹 Module 1 — ASK

## Agents

- Sinh viên NLP  
- ML Engineer  
- Data Scientist  
- Researcher  

---

## Selected Lenses

| Lens                   | Purpose                         |
|------------------------|---------------------------------|
| Dataset Overview       | Hiểu quy mô dữ liệu             |
| Validation Types       | Kiểm tra chất lượng dữ liệu     |
| Annotations & Labeling | Đánh giá độ tin cậy nhãn        |
| Transformations        | So sánh trước/sau xử lý         |
| Risks & Limitations    | Xác định rủi ro                 |
| Use in ML Systems      | Hướng dẫn sử dụng               |

---

## N/A Sections

| Section | Reason |
|--------|-------|
| Funding | N/A — dataset public |
| Human attributes | N/A — không có metadata |
| Access/Retention | N/A — không yêu cầu lab |
| Extended use | N/A — ngoài phạm vi bài |

---

# 🔹 Module 2 — INSPECT

## Checklist

| Item | Status |
|------|--------|
| Dataset stats | ✅ |
| GE validation | ✅ |
| Audit logs | ✅ |
| Cleanlab | ✅ |
| Manual review | ⚠️ |

---

## Metadata Register

| Field | Status |
|------|--------|
| n_rows | Verified |
| label_counts | Verified |
| duplicates | Verified |
| text_length | Verified |
| cleanlab_issues | Estimated |
| manual_review | To be measured |

---

# 🔹 Module 3 — ANSWER

---

## Dataset Overview

Dataset gồm 50,000 review phim, phân loại cảm xúc (positive/negative), cân bằng.

### Dataset Snapshot

| Category               | Data                |
|------------------------|---------------------|
| Number of Instances    | 50000               |
| Number of Fields       | 3                   |
| Labeled Classes        | 2                   |
| Train                  | 40000               |
| Validation             | 5000                |
| Test                   | 5000                |
| Class Distribution     | 25000 / 25000       |
| Duplicates             | 832 (~1.66%)        |
| Suspected Label Issues | 1000 (~2%)          |

---

## Descriptive Statistics

| Statistic | Value |
|-----------|------|
| min       | 32   |
| median    | 954  |
| p95       | 3328 |
| max       | 13593 |

---

## Validation Types (Great Expectations)

Dataset được kiểm tra bằng GE.

| Metric | Value |
|-------|------|
| Evaluated | 6 |
| Passed | 5 |
| Failed | 1 |
| Success Rate | 83.33% |

### Failed Rule

| Rule | Issue | Count |
|------|------|------|
| len_chars ≤ 10000 | vượt giới hạn | 6 |

 Nguyên nhân: tồn tại outliers  
 Xử lý: giữ lại hoặc truncate  

---

## Annotations & Labeling (Cleanlab)

Cleanlab phát hiện các mẫu nghi vấn.

| Metric | Value |
|-------|------|
| Suspected Issues | 1000 |
| Ratio | 2% |

### Manual Review (5 samples)

| ID | Label | Decision |
|----|------|---------|
| 11668 | 0 | Keep |
| 22259 | 1 | Keep |
| 16634 | 1 | Keep |
| 31245 | 0 | Ambiguous |
| 32355 | 1 | Ambiguous |

Kết luận: label noise tồn tại nhưng thấp

---

## Transformations

Dataset đã được làm sạch và chuẩn hóa.

### Applied
- Remove HTML tags  
- Normalize text  
- Dataset splitting  

### Before vs After

#### HTML

| Metric | Before | After |
|--------|--------|------|
| HTML tags | 29202 | 0 |
| HTML entities | 11 | 11 |

#### Length

| Metric | Before | After |
|--------|--------|------|
| median | 970 | 954 |
| max | 13704 | 13593 |

#### Duplicates

| Metric | Before | After |
|--------|--------|------|
| count | 824 | 832 |
| ratio | 0.01648 | 0.01664 |

 HTML được loại bỏ hoàn toàn  
 Phân phối dữ liệu giữ ổn định  

---

## Use in ML Systems

| Set | Size |
|----|------|
| Train | 40000 |
| Validation | 5000 |
| Test | 5000 |

---

## Risks & Limitations

| Risk | Description | Mitigation |
|------|------------|-----------|
| Duplicate | Overfitting | Deduplicate |
| Label noise | Sai nhãn | Review thêm |
| Outliers | Text dài | Truncate |
| Leakage | Sai pipeline | Fit train only |

---

# 🔹 Module 4 — AUDIT

## Heuristics Scorecard

| Criteria | Score | Reason |
|----------|------|--------|
| Completeness | 5 | Đầy đủ yêu cầu |
| Accuracy | 5 | Số liệu từ output |
| Clarity | 4 | Có thể gọn hơn |
| Timeliness | 5 | Dữ liệu mới |
| Actionability | 5 | Có hướng xử lý |

---

#  Final Conclusion

Dataset IMDB:
- ✔ cân bằng  
- ✔ sạch HTML  
- ⚠ còn duplicate, label noise và outliers  

 Phù hợp cho:
- học tập  
- research  

 Cần xử lý thêm nếu dùng production.