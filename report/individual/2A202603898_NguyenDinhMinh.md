# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV: 2A202603898**
- **Họ và tên: Nguyễn Đình Minh**
- **SEED** (in ở ô đầu notebook): 874

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | ☑ |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | ☑ |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | ☑ |

## 2. Kết quả chính

1. BoW + LogReg (tự code)            0.988   0.856      0.917        0.947   
2. BoW + MLP (deep learning)         0.989   0.928      0.957        1.000   
3a. Encoder (MiniLM) + kNN           0.879   0.969      0.922        0.923   
3b. Encoder (MiniLM) + LogReg        0.969   0.979      0.974        0.974   
3c. Encoder (MiniLM) + MLP head      0.979   0.979      0.979        1.000   
4a. LLM nhỏ zero-shot                0.800   1.000      0.889        0.889   
4b. LLM lớn zero-shot                0.833   1.000      0.909        0.909   
4c. LLM nhỏ few-shot                 0.947   0.900      0.923        0.923   

                                 train (s)  tin/s (cả lô)  p50 ms/tin  \
1. BoW + LogReg (tự code)            4.815      11455.813       0.035   
2. BoW + MLP (deep learning)         7.879      42098.104       0.212   
3a. Encoder (MiniLM) + kNN          55.896         46.950      36.915   
3b. Encoder (MiniLM) + LogReg       56.112         70.398      24.720   
3c. Encoder (MiniLM) + MLP head     56.712         70.202      23.854   
4a. LLM nhỏ zero-shot                0.000          0.815     759.565   
4b. LLM lớn zero-shot                0.000          0.921     613.885   
4c. LLM nhỏ few-shot                 0.000          0.785     699.975   

                                 p95 ms/tin  USD / 1k tin  
1. BoW + LogReg (tự code)             0.063           0.0  
2. BoW + MLP (deep learning)          0.386           0.0  
3a. Encoder (MiniLM) + kNN           47.557           0.0  
3b. Encoder (MiniLM) + LogReg        41.353           0.0  
3c. Encoder (MiniLM) + MLP head      29.176           0.0  
4a. LLM nhỏ zero-shot              2728.871           0.0  
4b. LLM lớn zero-shot              2779.552           0.0  
4c. LLM nhỏ few-shot               2983.915           0.0  
• Hàng LLM chỉ đo trên SUB (40 tin) → so sánh chất lượng công bằng bằng cột 'F1 (SUB 40)'.
• SUB chỉ 40 tin: 1 tin sai đổi F1 vài điểm. Chênh < ~0.05 F1 coi như HOÀ — đừng xếp hạng theo số lẻ.
• Inference đo TỪ VĂN BẢN THÔ → NHÃN (gồm cả vectorize / encode). p50/p95 = gọi từng tin một, như một request thật.
• train (s) của 3a/3b/3c = thời gian encoder MiniLM encode tập train (+ train đầu LogReg / MLP); LLM = 0 vì không train. Số đo phụ thuộc CPU/GPU của Colab.

## 3. Dự đoán và thực tế

*Chọn 3 dự đoán `predict(...)` lệch nhiều nhất so với kết quả. Mỗi cái: bạn đoán gì, ra gì, vì sao lệch.*

## 4. Phân tích 50 case khó

*Model nào tụt nhiều nhất, ở nhóm case nào? Nêu 2 case cụ thể và cơ chế khiến model sai.*

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học
Mình thiếu nhiều kiến thức nền tảng nên đã sử dụng AI rất nhiều
*Mỗi lần dùng AI: hỏi gì, nhận gì, bạn sửa gì. Sau đó 2–3 câu: điều bạn hiểu ra hôm nay mà trước đó chưa hiểu.*
