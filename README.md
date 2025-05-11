# Dự án Dự đoán Giá Cổ Phiếu (MBB, FPT, HAG, HPG, VNM)

## Tổng quan
Dự án xây dựng hệ thống dự đoán giá cổ phiếu từ 10/04/2025 đến 10/04/2028 cho 5 cổ phiếu: **MBB**, **FPT**, **HAG**, **HPG**, và **VNM**. Hệ thống sử dụng **Prophet** (dự đoán giá đầu tháng) và **LSTM** (dự đoán giá ngày), tích hợp các yếu tố:
- **Chỉ số thị trường**: S&P 500 và VNINDEX.
- **Chỉ số ngành**: Tính từ giá cổ phiếu cùng ngành, gia quyền theo vốn hóa thị trường.

Dự án được thực hiện từ 01/05/2025 đến 08/05/2025, bao gồm xử lý dữ liệu, xây dựng mô hình, trực quan hóa.

[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

## Mục lục
- [Cấu trúc thư mục](#cấu-trúc-thư-mục)
- [Quy trình thực hiện](#quy-trình-thực-hiện)
  - [Bước 1: Dự đoán S&P 500 và VNINDEX](#bước-1-dự-đoán-s&p-500-và-vnindex)
  - [Bước 2: Dự đoán chỉ số ngành](#bước-2-dự-đoán-chỉ-số-ngành)
  - [Bước 3: Dự đoán cổ phiếu đích](#bước-3-dự-đoán-cổ-phiếu-đích)
  - [Bước 4: Trực quan hóa và đánh giá](#bước-4-trực-quan-hóa-và-đánh-giá)
- [Cách chạy code](#cách-chạy-code)
- [Thông tin bổ sung](#thông-tin-bổ-sung)
- [Liên hệ](#liên-hệ)

## Cấu trúc thư mục
Dự án được tổ chức như sau:

```
📦 Financial Market Forecasting Project
├── S&P500 & VNINDEX/
│   ├── S&P500 & VNINDEX.ipynb
│   ├── S&P500_DAY.csv
│   ├── S&P500_MONTH.csv
│   ├── SP500_Daily_Predictions_2024_2028.csv
│   ├── SP500_Daily_Predictions_2025_2028.csv
│   ├── SP500_Full_Predictions_2015_2028.csv
│   ├── SP500_Prediction_Chart_Full.png
│   ├── SP500_Prediction_Chart_Detail_2025_2028.png
│   ├── VNINDEX_DAY.csv
│   ├── VNINDEX_MONTH.csv
│   ├── VNINDEX_Full_Predictions_2015_2028.csv
│   ├── VNINDEX_Prediction_Chart_Full.png
│   ├── VNINDEX_Prediction_Chart_Detail_2025_2028.png
├── MBB/
│   ├── MBB.ipynb
│   ├── MBB.csv
│   ├── Dữ liệu Lịch sử BID 245.41T.csv
│   ├── Dữ liệu Lịch sử VCB 481.92T.csv
│   ├── Dữ liệu Lịch sử CTG 201.91T.csv
│   ├── Dữ liệu Lịch sử TCB 190.04T.csv
│   ├── Banking_Industry_Index_Prediction.ipynb
│   ├── Banking_Industry_Historical.csv
│   ├── Banking_Industry_Monthly_Forecast.csv
│   ├── Banking_Industry_Daily_Predictions.csv
│   ├── Banking_Industry_Prediction_Chart.png
│   ├── MBB_Daily_Processed.csv
│   ├── MBB_Monthly_Processed.csv
│   ├── MBB_Full_Predictions_2020_2028.csv
│   ├── MBB_Prediction_Chart_Full.png
│   ├── MBB_Prediction_Chart_Detail_2025_2028.png
│   ├── SP500_Full_Predictions_2015_2028.csv
│   ├── VNINDEX_Full_Predictions_2015_2028.csv
├── FPT/
│   ├── FPT.ipynb
│   ├── FPT.csv
│   ├── Dữ liệu Lịch sử CMG 7.06T.csv
│   ├── Dữ liệu Lịch sử ELC 2.18T.csv
│   ├── Dữ liệu Lịch sử SGT 2.68T.csv
│   ├── Technology_Industry_Index_Prediction.ipynb
│   ├── Technology_Industry_Historical.csv
│   ├── Technology_Industry_Monthly_Forecast.csv
│   ├── Technology_Industry_Daily_Predictions.csv
│   ├── Technology_Industry_Prediction_Chart.png
│   ├── FPT_Daily_Processed.csv
│   ├── FPT_Monthly_Processed.csv
│   ├── FPT_Full_Predictions_2020_2028.csv
│   ├── FPT_Prediction_Chart_Full.png
│   ├── FPT_Prediction_Chart_Detail_2025_2028.png
│   ├── SP500_Full_Predictions_2015_2028.csv
│   ├── VNINDEX_Full_Predictions_2015_2028.csv
├── HAG/
│   ├── HAG.ipynb
│   ├── HAG.csv
│   ├── Dữ liệu Lịch sử BAF 10.63T.csv
│   ├── Dữ liệu Lịch sử DBG 9.22T.csv
│   ├── Dữ liệu Lịch sử LTG 2318.8B.csv
│   ├── Dữ liệu Lịch sử PAN 4.82T.csv
│   ├── Agriculture_Industry_Index_Prediction.ipynb
│   ├── Agriculture_Industry_Historical.csv
│   ├── Agriculture_Industry_Monthly_Forecast.csv
│   ├── Agriculture_Industry_Daily_Predictions.csv
│   ├── Agriculture_Industry_Prediction_Chart.png
│   ├── HAG_Daily_Processed.csv
│   ├── HAG_Monthly_Processed.csv
│   ├── HAG_Full_Predictions_2020_2028.csv
│   ├── HAG_Prediction_Chart_Full.png
│   ├── HAG_Prediction_Chart_Detail_2025_2028.png
│   ├── SP500_Full_Predictions_2015_2028.csv
│   ├── VNINDEX_Full_Predictions_2015_2028.csv
├── HPG/
│   ├── HPG.ipynb
│   ├── HPG.csv
│   ├── Dữ liệu Lịch sử HSG 9T.csv
│   ├── Dữ liệu Lịch sử HT1 4.16T.csv
│   ├── Dữ liệu Lịch sử NKG 5.51T.csv
│   ├── Dữ liệu Lịch sử TLH 624.85B.csv
│   ├── Steel_Industry_Index_Prediction.ipynb
│   ├── Steel_Industry_Historical.csv
│   ├── Steel_Industry_Monthly_Forecast.csv
│   ├── Steel_Industry_Daily_Predictions.csv
│   ├── Steel_Industry_Prediction_Chart.png
│   ├── HPG_Daily_Processed.csv
│   ├── HPG_Monthly_Processed.csv
│   ├── HPG_Full_Predictions_2020_2028.csv
│   ├── HPG_Prediction_Chart_Full.png
│   ├── HPG_Prediction_Chart_Detail_2025_2028.png
│   ├── SP500_Full_Predictions_2015_2028.csv
│   ├── VNINDEX_Full_Predictions_2015_2028.csv
├── VNM/
│   ├── VNM.ipynb
│   ├── VNM.csv
│   ├── Dữ liệu Lịch sử BHN 8.81T.csv
│   ├── Dữ liệu Lịch sử KDC 16.27T.csv
│   ├── Dữ liệu Lịch sử SAB 61.88T.csv
│   ├── Dữ liệu Lịch sử SBT 13.6T.csv
│   ├── Consumer_Industry_Index_Prediction.ipynb
│   ├── Consumer_Industry_Historical.csv
│   ├── Consumer_Industry_Monthly_Forecast.csv
│   ├── Consumer_Industry_Daily_Predictions.csv
│   ├── Consumer_Industry_Prediction_Chart.png
│   ├── VNM_Daily_Processed.csv
│   ├── VNM_Monthly_Processed.csv
│   ├── VNM_Full_Predictions_2020_2028.csv
│   ├── VNM_Prediction_Chart_Full.png
│   ├── VNM_Prediction_Chart_Detail_2025_2028.png
│   ├── SP500_Full_Predictions_2015_2028.csv
│   ├── VNINDEX_Full_Predictions_2015_2028.csv
```

### Vốn hóa thị trường (ước tính từ Investing.com, 10/04/2025)
- **Ngân hàng**: MBB: 120,000 tỷ VND, BID: 300,000 tỷ VND, VCB: 500,000 tỷ VND, CTG: 200,000 tỷ VND, TCB: 150,000 tỷ VND.
- **Công nghệ**: FPT: 161,380 tỷ VND, CMG: 7,060 tỷ VND, ELC: 2,180 tỷ VND, SGT: 2,680 tỷ VND.
- **Nông nghiệp**: HAG: 13,900 tỷ VND, BAF: 10,630 tỷ VND, DBC: 9,220 tỷ VND, PAN: 4,820 tỷ VND.
- **Thép**: HPG: 162,460 tỷ VND, HSG: 9,000 tỷ VND, HT1: 4,160 tỷ VND, NKG: 5,510 tỷ VND, TLH: 625 tỷ VND.
- **Thực phẩm đồ uống**: VNM: 119,550 tỷ VND, BHN: 8,810 tỷ VND, KDC: 16,200 tỷ VND, SAB: 61,880 tỷ VND, SBT: 13,600 tỷ VND.

### Cổ phiếu cùng ngành
- **Ngân hàng (MBB)**: BID, VCB, CTG, TCB.
- **Công nghệ (FPT)**: CMG, SGT, ELC.
- **Nông nghiệp (HAG)**: DBC, BAF, LTG, PAN.
- **Thép (HPG)**: HSG, NKG, HT1, TLH.
- **Thực phẩm đồ uống (VNM)**: SAB, KDC, SBT, BHN.

## Quy trình thực hiện

### Bước 1: Dự đoán S&P 500 và VNINDEX
- **Mục tiêu**: Dự đoán S&P 500 và VNINDEX từ 2015-2028 để làm đặc trưng đầu vào.
- **File liên quan**: `S&P500 & VNINDEX/S&P500 & VNINDEX.ipynb`
- **Hoạt động**:
  1. Đọc dữ liệu lịch sử (`S&P500_DAY.csv`, `S&P500_MONTH.csv`, `VNINDEX_DAY.csv`, `VNINDEX_MONTH.csv`) từ 01/01/2015 đến 09/04/2025.
  2. Sử dụng **Prophet** để dự đoán giá đầu tháng từ 10/04/2025 đến 10/04/2028.
  3. Sử dụng **LSTM** (cửa sổ trượt `time_step=300`) để dự đoán giá ngày, điều chỉnh tuyến tính để khớp với giá đầu tháng.
  4. Điền giá trị thiếu bằng phương pháp `ffill`.
  5. Lưu kết quả:
     - `SP500_Full_Predictions_2015_2028.csv`
     - `VNINDEX_Full_Predictions_2015_2028.csv`
     - `SP500_Daily_Predictions_2024_2028.csv`, `SP500_Daily_Predictions_2025_2028.csv` (kết quả trung gian)
  6. Tạo biểu đồ:
     - `SP500_Prediction_Chart_Full.png`, `SP500_Prediction_Chart_Detail_2025_2028.png`
     - `VNINDEX_Prediction_Chart_Full.png`, `VNINDEX_Prediction_Chart_Detail_2025_2028.png`

### Bước 2: Dự đoán chỉ số ngành
- **Mục tiêu**: Tính và dự đoán chỉ số ngành để làm đặc trưng đầu vào.
- **File liên quan**:
  - `MBB/Banking_Industry_Index_Prediction.ipynb`
  - `FPT/Technology_Industry_Index_Prediction.ipynb`
  - `HAG/Agriculture_Industry_Index_Prediction.ipynb`
  - `HPG/Steel_Industry_Index_Prediction.ipynb`
  - `VNM/Consumer_Industry_Index_Prediction.ipynb`
- **Hoạt động** (ví dụ: ngành Ngân hàng):
  1. Đọc dữ liệu cổ phiếu cùng ngành (`MBB.csv`, `Dữ liệu Lịch sử BID 245.41T.csv`, v.v.) từ 10/04/2020 đến 09/04/2025.
  2. Tính chỉ số ngành (trung bình gia quyền theo vốn hóa):
     ```python
     total_cap = sum(capitalization.values())
     industry_data['Banking_Industry_Index'] = sum(industry_data[f'{stock}_Price'] * (capitalization[stock] / total_cap) for stock in stocks.keys())
     ```
  3. Sử dụng **Prophet** để dự đoán chỉ số đầu tháng từ 10/04/2025 đến 10/04/2028.
  4. Sử dụng **LSTM** để dự đoán chỉ số ngày, điều chỉnh tuyến tính để khớp với giá đầu tháng.
  5. Lưu kết quả:
     - `Banking_Industry_Historical.csv`
     - `Banking_Industry_Monthly_Forecast.csv`
     - `Banking_Industry_Daily_Predictions.csv`
  6. Tạo biểu đồ: `Banking_Industry_Prediction_Chart.png`
- **Lặp lại** cho các ngành: Công nghệ, Nông nghiệp, Thép, Thực phẩm đồ uống.

### Bước 3: Dự đoán cổ phiếu đích
- **Mục tiêu**: Dự đoán giá cổ phiếu MBB, FPT, HAG, HPG, VNM.
- **File liên quan**:
  - `MBB/MBB.ipynb`, `FPT/FPT.ipynb`, `HAG/HAG.ipynb`, `HPG/HPG.ipynb`, `VNM/VNM.ipynb`
- **Hoạt động** (ví dụ: MBB):
  1. Đọc dữ liệu giá (`MBB.csv`) từ 10/04/2020 đến 10/04/2025.
  2. Ghép với dữ liệu S&P 500 (`SP500_Full_Predictions_2015_2028.csv`), VNINDEX (`VNINDEX_Full_Predictions_2015_2028.csv`), và chỉ số ngành (`Banking_Industry_Daily_Predictions.csv`).
  3. Tạo dữ liệu đầu tháng và ngày đã xử lý, lưu vào:
     - `MBB_Daily_Processed.csv`
     - `MBB_Monthly_Processed.csv`
  4. Sử dụng **Prophet** để dự đoán giá đầu tháng từ 10/04/2025 đến 10/04/2028, với đặc trưng S&P 500, VNINDEX, chỉ số ngành.
  5. Sử dụng **LSTM** (cửa sổ trượt `time_step=300`) để dự đoán giá ngày, điều chỉnh tuyến tính để khớp với giá đầu tháng.
  6. Lưu kết quả: `MBB_Full_Predictions_2020_2028.csv`
  7. Tạo biểu đồ:
     - `MBB_Prediction_Chart_Full.png` (tổng quan 2020-2028)
     - `MBB_Prediction_Chart_Detail_2025_2028.png` (chi tiết 2025-2028)
- **Lặp lại** cho FPT, HAG, HPG, VNM.

### Bước 4: Trực quan hóa và đánh giá
- **Trực quan hóa**: Biểu đồ tổng quan (2020-2028) và chi tiết (2025-2028) cho S&P 500, VNINDEX, chỉ số ngành, và mỗi cổ phiếu.
- **Đánh giá**: Tính RMSE/MAE trên tập kiểm tra (01/01/2025 - 10/04/2025) để đánh giá độ chính xác.
- **Cải tiến tiềm năng**:
  - Tích hợp chỉ số tài chính (Revenue, Net Profit, P/E, ROE).
  - Thêm yếu tố vĩ mô (lãi suất, tỷ giá).
  - Sử dụng mô hình Transformer thay thế LSTM.

## Cách chạy code

### Yêu cầu
- Python 3.8+
- Thư viện: `pandas`, `numpy`, `prophet`, `torch`, `matplotlib`, `scikit-learn`.
- Cài đặt:
  ```bash
  pip install pandas numpy prophet torch matplotlib scikit-learn
  ```
- Môi trường: Jupyter Notebook để chạy các file `.ipynb`.

### Hướng dẫn chạy
Để chạy dự án, thực hiện các bước sau theo đúng thứ tự để đảm bảo phụ thuộc dữ liệu:

1. **Chuẩn bị dữ liệu**:
   - Đảm bảo tất cả file CSV (`S&P500_DAY.csv`, `MBB.csv`, `Dữ liệu Lịch sử BID 245.41T.csv`, v.v.) được đặt đúng trong các thư mục tương ứng (`S&P500 & VNINDEX/`, `MBB/`, `FPT/`, v.v.).
   - Kiểm tra các file dữ liệu có định dạng đúng (cột `Date`, `Price` hoặc `Lần cuối`, không có giá trị bất thường).

2. **Dự đoán S&P 500 và VNINDEX**:
   - **File**: `S&P500 & VNINDEX/S&P500 & VNINDEX.ipynb`
   - **Hành động**:
     1. Mở Jupyter Notebook:
        ```bash
        jupyter notebook
        ```
     2. Điều hướng đến thư mục `S&P500 & VNINDEX/` và mở `S&P500 & VNINDEX.ipynb`.
     3. Chạy từng cell trong notebook (Shift + Enter).
   - **Kết quả**:
     - Tạo file: `SP500_Full_Predictions_2015_2028.csv`, `VNINDEX_Full_Predictions_2015_2028.csv`, và các biểu đồ.
     - Các file này sẽ được sử dụng trong các bước tiếp theo.

3. **Dự đoán chỉ số ngành**:
   - **File**:
     - `MBB/Banking_Industry_Index_Prediction.ipynb`
     - `FPT/Technology_Industry_Index_Prediction.ipynb`
     - `HAG/Agriculture_Industry_Index_Prediction.ipynb`
     - `HPG/Steel_Industry_Index_Prediction.ipynb`
     - `VNM/Consumer_Industry_Index_Prediction.ipynb`
   - **Hành động**:
     1. Trong Jupyter Notebook, điều hướng đến thư mục tương ứng (ví dụ: `MBB/`).
     2. Mở file (ví dụ: `Banking_Industry_Index_Prediction.ipynb`).
     3. Chạy từng cell trong notebook.
     4. Lặp lại cho các ngành khác (`Technology_Industry_Index_Prediction.ipynb`, v.v.).
   - **Kết quả** (ví dụ: ngành Ngân hàng):
     - Tạo file: `Banking_Industry_Historical.csv`, `Banking_Industry_Monthly_Forecast.csv`, `Banking_Industry_Daily_Predictions.csv`.
     - Tạo biểu đồ: `Banking_Industry_Prediction_Chart.png`.
   - **Lưu ý**: Đảm bảo `SP500_Full_Predictions_2015_2028.csv` và `VNINDEX_Full_Predictions_2015_2028.csv` đã được tạo từ bước trước.

4. **Dự đoán cổ phiếu đích**:
   - **File**:
     - `MBB/MBB.ipynb`
     - `FPT/FPT.ipynb`
     - `HAG/HAG.ipynb`
     - `HPG/HPG.ipynb`
     - `VNM/VNM.ipynb`
   - **Hành động**:
     1. Trong Jupyter Notebook, điều hướng đến thư mục tương ứng (ví dụ: `MBB/`).
     2. Mở file (ví dụ: `MBB.ipynb`).
     3. Chạy từng cell trong notebook.
     4. Lặp lại cho các cổ phiếu khác (`FPT.ipynb`, v.v.).
   - **Kết quả** (ví dụ: MBB):
     - Tạo file: `MBB_Daily_Processed.csv`, `MBB_Monthly_Processed.csv`, `MBB_Full_Predictions_2020_2028.csv`.
     - Tạo biểu đồ: `MBB_Prediction_Chart_Full.png`, `MBB_Prediction_Chart_Detail_2025_2028.png`.
   - **Lưu ý**: Đảm bảo file dự đoán chỉ số ngành (ví dụ: `Banking_Industry_Daily_Predictions.csv`) đã được tạo từ bước trước.

5. **Kiểm tra kết quả**:
   - Mở các file CSV (`MBB_Full_Predictions_2020_2028.csv`, v.v.) để xem dữ liệu dự đoán.
   - Xem các biểu đồ PNG (`MBB_Prediction_Chart_Full.png`, v.v.) để kiểm tra trực quan hóa.

## Thông tin bổ sung
- **Thời gian thực hiện**: 01/05/2025 - 08/05/2025.
- **Nguồn dữ liệu**: Giá cổ phiếu, S&P 500, VNINDEX từ [Investing.com](https://vn.investing.com/).
- **Hạn chế**:
  - Giá trị thiếu được điền bằng `ffill`, có thể làm giảm độ nhạy với biến động.
  - Chỉ số ngành sử dụng vốn hóa cố định, chưa phản ánh thay đổi theo thời gian.
- **Cải tiến tương lai**:
  - Tích hợp chỉ số tài chính (Revenue, Net Profit, P/E, ROE).
  - Cập nhật vốn hóa thị trường động.
  - Thử nghiệm mô hình Transformer thay thế LSTM.

## Liên hệ
- **Người thực hiện**: Hoàng Bùi Tuấn Anh, Trần Đức Anh, Vũ Thục Linh, Trần Hồng Đăng
- **GitHub**: [https://github.com/hoangbuituananh132109/long-term-stock-price-prediction-with-LSTM](https://github.com/hoangbuituananh132109/long-term-stock-price-prediction-with-LSTM)
