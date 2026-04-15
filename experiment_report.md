# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600153
**Name:** Nguyễn Duy Hiếu
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | Pipeline đã loại bỏ thành công các bản ghi lỗi (ID 3, ID 4), giúp Agent đưa ra kết quả chính xác dựa trên dữ liệu sạch. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Agent bị đánh lừa bởi giá trị ngoại lai (Outlier) cực lớn và không thể phân biệt được dữ liệu vô lý. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Việc sử dụng dữ liệu rác (Garbage Data) đã bộc lộ những điểm yếu chí mạng của AI Agent trong việc xử lý thông tin. Nguyên nhân chính khiến Agent trả lời sai là do các giá trị ngoại lai (**Extreme Outliers**) như "Nuclear Reactor" với mức giá $999,999; vì logic của Agent là tìm kiếm sản phẩm có giá cao nhất trong chuyên mục, nó đã mặc định coi đây là lựa chọn "tốt nhất" mà không có khả năng kiểm chứng tính thực tế.

Bên cạnh đó, các vấn đề như **Duplicate IDs** (ID 1 dùng cho cả Laptop và Banana) gây nhiễu loạn định danh sản phẩm, trong khi **Wrong data types** (giá trị dạng chữ "ten dollars" thay vì số) khiến các phép toán so sánh bị lỗi hoặc bỏ qua. Các giá trị **Null** cũng khiến Agent mất đi ngữ cảnh phân loại, dẫn đến việc không thể xác định đúng đối tượng khách hàng yêu cầu. Tóm lại, nếu không có bước ETL làm sạch như trong `solution.py`, Agent sẽ trở nên thiếu tin cậy và đưa ra thông tin sai lệch cho người dùng.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

**Hoàn toàn đồng ý.** Dù bạn có viết Prompt tối ưu và tinh tế đến đâu nhưng nếu dữ liệu đầu vào (Knowledge Base) bị "nhiễm độc" bởi các giá trị sai lệch, Agent vẫn sẽ đưa ra kết quả sai (Garbage In, Garbage Out). Việc đảm bảo chất lượng dữ liệu thông qua Pipeline ETL là nền tảng quan trọng nhất để xây dựng một hệ thống AI đáng tin cậy.