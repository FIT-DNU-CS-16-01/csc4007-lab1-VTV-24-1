# Dataset Name (IMDB)

IMDB dataset là tập dữ liệu review phim dùng cho bài toán sentiment analysis. Dataset gồm các đoạn văn bản (review) được gán nhãn positive/negative. Đây là dataset phổ biến trong NLP research, phù hợp cho bài toán phân loại văn bản, tuy nhiên vẫn tồn tại duplicate, label noise và outliers cần xử lý trước khi sử dụng production.

---

#### Dataset Link
N/A — dataset sử dụng từ nguồn public (IMDB/Kaggle).

---

#### Data Card Author(s)
- N/A — Owner
- N/A — Contributor
- N/A — Manager

---

## Authorship
### Publishers
#### Publishing Organization(s)
N/A — dataset public.

#### Industry Type(s)
- Academic - Tech

#### Contact Detail(s)
- Publishing POC: N/A  
- Affiliation: N/A  
- Contact: N/A  
- Mailing List: N/A  
- Website: N/A  

---

### Dataset Owners
#### Team(s)
N/A — dataset public.

#### Contact Detail(s)
- Dataset Owner(s): N/A  
- Affiliation: N/A  
- Contact: N/A  
- Group Email: N/A  
- Website: N/A  

#### Author(s)
- N/A

---

### Funding Sources
#### Institution(s)
- N/A

#### Funding or Grant Summary(ies)
N/A — không có thông tin funding.

**Additional Notes:** Dataset public.

---

## Dataset Overview
#### Data Subject(s)
- Non-Sensitive Data about people

---

#### Dataset Snapshot

| Category | Data |
|----------|------|
| Size of Dataset | N/A |
| Number of Instances | 50000 |
| Number of Fields | 3 |
| Labeled Classes | 2 |
| Number of Labels | 50000 |
| Average Labels Per Instance | 1 |
| Algorithmic Labels | 0 |
| Human Labels | 50000 |
| Other Characteristics | text data |

**Above:** Snapshot tổng quan dataset IMDB.

**Additional Notes:** Dữ liệu cân bằng 50/50.

---

#### Content Description
Dataset gồm các review phim dạng text.

**Additional Notes:** Không có missing values.

---

#### Descriptive Statistics

Statistic | text_length
--- | ---
min | 32
median | 954
p95 | 3328
max | 13593

**Above:** Thống kê độ dài text.

**Additional Notes:** Có outliers >10000.

---

### Sensitivity of Data
#### Sensitivity Type(s)
- None

---

#### Field(s) with Sensitive Data

**Intentional Collected Sensitive Data**

N/A — dataset không chứa dữ liệu nhạy cảm.

**Unintentionally Collected Sensitive Data**

N/A — không có dữ liệu suy luận nhạy cảm.

**Additional Notes:** Review công khai.

---

#### Security and Privacy Handling
N/A — không có dữ liệu nhạy cảm.

---

#### Risk Type(s)
- Indirect Risk
- Residual Risk

---

#### Supplemental Link(s)
N/A

---

#### Risk(s) and Mitigation(s)

- Duplicate → deduplicate  
- Label noise → review thêm  
- Outliers → truncate  
- Leakage → fit train only  

---

### Dataset Version and Maintenance
#### Maintenance Status
Limited Maintenance

---

#### Version Details
- Current Version: 1.0  
- Last Updated: 04/2026  
- Release Date: N/A  

---

#### Maintenance Plan
N/A — dataset static.

---

#### Next Planned Update(s)
N/A

---

#### Expected Change(s)
N/A

---

## Example of Data Points
#### Primary Data Modality
- Text Data

---

#### Sampling of Data Points
N/A

---

#### Data Fields

| Field Name | Description |
|------------|------------|
| id | ID |
| text | review |
| label | sentiment |

---

#### Typical Data Point
N/A

---

#### Atypical Data Point
N/A

---

## Motivations & Intentions
### Motivations
#### Purpose(s)
- Research

---

#### Domain(s) of Application
`NLP`, `Sentiment Analysis`

---

#### Motivating Factor(s)
Dataset phục vụ huấn luyện model phân loại cảm xúc văn bản.

---

### Intended Use
#### Dataset Use(s)
- Safe for research use

---

#### Suitable Use Case(s)
- Sentiment classification  
- NLP research  

---

#### Unsuitable Use Case(s)
- Production khi chưa clean  
- Task ngoài sentiment  

---

#### Research and Problem Space(s)
Phân loại cảm xúc văn bản.

---

#### Citation Guidelines
N/A

---

## Access, Rentention, & Wipeout
### Access
#### Access Type
- External - Open Access

---

#### Documentation Link(s)
N/A

---

#### Prerequisite(s)
N/A

---

#### Policy Link(s)
N/A

---

#### Access Control List(s)
N/A

---

### Retention
#### Duration
N/A

#### Policy Summary
N/A

#### Process Guide
N/A

#### Exception(s) and Exemption(s)
N/A

---

### Wipeout and Deletion
#### Duration
N/A

#### Deletion Event Summary
N/A

#### Acceptable Means of Deletion
N/A

#### Post-Deletion Obligations
N/A

#### Operational Requirement(s)
N/A

#### Exceptions and Exemptions
N/A

---

## Provenance
### Collection
#### Method(s) Used
- Taken from other existing datasets

---

#### Methodology Detail(s)
N/A — dataset public.

---

#### Source Description(s)
- Public IMDB reviews dataset

---

#### Collection Cadence
- Static

---

## Transformations
### Synopsis
#### Transformation(s) Applied
- Cleaning Mismatched Values

---

#### Field(s) Transformed

| Field Name | Source & Target |
|------------|----------------|
| text | raw → cleaned |

---

#### Library(ies) and Method(s) Used

- Remove HTML tags  
- Normalize text  

---

#### Comparative Summary

| Metric | Before | After |
|--------|--------|------|
| HTML tags | 29202 | 0 |
| median length | 970 | 954 |

---

#### Residual & Other Risk(s)

- Duplicate (~1.6%)  
- Label noise (~2%)  
- Outliers  

---

## Annotations & Labeling
#### Annotation Workforce Type
- Machine-Generated

---

#### Annotation Distribution(s)

| Label | Count |
|------|------|
| 0 | 25000 |
| 1 | 25000 |

---

## Validation Types
#### Method(s)
- Data Type Validation  
- Range Validation  
- Consistency Validation  

---

#### Breakdown(s)
- Evaluated: 6  
- Passed: 5  
- Failed: 1  

---

## Sampling Methods
#### Method(s) Used
- Random Sampling

---

## Known Applications & Benchmarks
#### ML Application(s)
Classification

---

## Reflections on Data

Dataset phù hợp cho nghiên cứu NLP nhưng cần xử lý thêm trước khi dùng production do tồn tại duplicate, noise và outliers.