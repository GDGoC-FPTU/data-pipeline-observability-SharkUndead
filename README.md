[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574056&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** nguyenduyhieu03112003@gmail.com
**Name:** Nguyễn Duy Hiếu

---

## Mo ta

Dự án này xây dựng một **Automated ETL Pipeline** hoàn chỉnh để xử lý dữ liệu thô cho các hệ thống AI.

Pipeline thực hiện các nhiệm vụ:
- Trích xuất dữ liệu từ JSON  
- Kiểm tra chất lượng (**Validation**)  
- Biến đổi dữ liệu (**Transformation**)  
- Lưu trữ dữ liệu sạch vào CSV  

🎯 **Mục tiêu:**
- Loại bỏ dữ liệu "độc hại" (*toxic data*)  
- Đánh giá ảnh hưởng của chất lượng dữ liệu đến phản hồi của AI Agent

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python generate_garbage.py
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # Script xử lý ETL chính
├── processed_data.csv       # Kết quả dữ liệu sạch
├── experiment_report.md     # Báo cáo phân tích
├── generate_garbage.py      # Tạo dữ liệu lỗi
├── agent_simulation.py      # Mô phỏng AI
└── README.md                # Tài liệu dự án
```

---

## Ket qua

Dựa trên kết quả thực tế:

- Tổng số bản ghi: **5 records**  
- Hợp lệ: **3 records**  
- Bị loại: **2 records**  
  - Giá ≤ 0  
