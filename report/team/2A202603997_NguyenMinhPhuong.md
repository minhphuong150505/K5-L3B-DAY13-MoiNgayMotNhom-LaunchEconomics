# Báo cáo cá nhân — NguyenMinhPhuong-2A202603997

## 1. Thông tin thành viên

- Họ tên: Nguyễn Minh Phương
- MSSV: `2A202603997`
- Email: `phuongnm150505@gmail.com`
- Vai trong nhóm: Người viết code · Trưởng nhóm (Team Lead & Core Dev)

## 2. Phần việc phụ trách

- Thiết lập repository nhóm `K5-L3B-DAY13-MoiNgayMotNhom-LaunchEconomics`, môi trường Python (`pandas`, `numpy`, `scipy`, `statsmodels`, `pyyaml`) và phân nhánh/quản lý Git theo quy tắc chống xung đột file.
- Hoàn thiện toàn bộ mã nguồn phân tích trong `src/lab13.py` (giữ nguyên bản gốc `src/lab13_starter.py` và hai file CSV):
  - **CP1 (Nhiệm vụ A1–A4):** 3 hàm kinh tế chạy lại (vượt qua cổng A1 `1,20 · 1,25 · 1,25`), mô hình chi phí từ trace `mo_hinh(...)`, tách chi phí và tỉ lệ `ok` theo lần thử cho 4 loại yêu cầu (`noi_dia`, `hang_nang`, `quoc_te`, `doi_tac`), và cộng chi phí cố định 40 triệu đ/tháng cho phạm vi pilot (`noi_dia` + `hang_nang`).
  - **CP2 (Nhiệm vụ B1–B4):** bảng độ nhạy 9 kịch bản đơn yếu tố, kịch bản đổi cặp (giá token gấp đôi + tỉ lệ xem lại gấp đôi), phân tích chi phí cả hệ thống cho giới hạn 1/2/3 lần chạy, và phân tích kịch bản xem lại 100% kèm độ nhạy thời gian làm lại thực từ dữ liệu.
  - **CP4 (Nhiệm vụ D1) & tham chiếu E1:** tính cỡ mẫu thống kê theo 5 câu D1, kiểm chứng chéo bằng `statsmodels.stats.power.NormalIndPower`, tính power thực tế ở mức chênh 5 điểm, và xuất các chỉ số đợt chạy thử (lưu ý không có nhóm đối chứng) để đồng bộ với các thành viên viết hồ sơ.
- Viết bộ kiểm thử tự động `tests/test_lab13.py` kiểm chứng toàn bộ hàm và kết quả trên cả dữ liệu tổng hợp lẫn dữ liệu giả lập `logix_runs.csv` và `logix_requests.csv`.

## 3. Đóng góp cụ thể

- **Cổng A1:** Cài đặt `so_lan_chay_ky_vong`, `ti_le_thanh_cong`, `he_so_chi_phi_moi_viec_thanh_cong` và vượt qua 3/3 phép thử bắt buộc (`1,20`, `1,25`, `1,25`).
- **Mô hình chi phí A2–A4:**
  - Tính tổng chi phí 4.373.585 đ (`token` 245.585 đ, `tool` 84.000 đ, trong đó chạy lại 93.804 đ đo từ trace; `xem_lai` 1.780.000 đ `simulated`; `lam_lai` 2.264.000 đ `simulated`) trên 978 việc thành công → chi phí mỗi việc thành công **4.472 đ** (`simulated`), gấp **16,3 lần** hoá đơn token+tool mỗi yêu cầu (274,7 đ). Chi phí cả hệ thống/yêu cầu là **5.865 đ** (`0,49×` mức 12.000 đ, `simulated`).
  - Phân tích theo loại cho thấy `quoc_te` không đáng chạy (22.515 đ = `1,88×`, `simulated`; tỉ lệ `ok` giảm từ 30,0% ở lần 1 xuống 11,4% ở lần 2 và 2,2% ở lần 3); `doi_tac` sát ngưỡng (10.215 đ = `0,85×`, `simulated`). Phạm vi pilot hợp lý là `noi_dia` (2.696 đ = `0,22×`, `simulated`) + `hang_nang` (8.221 đ = `0,69×`, `simulated`).
  - Cộng chi phí cố định 40 triệu đ/tháng trong phạm vi `noi_dia` + `hang_nang`: 4.599 đ (`0,38×`, `simulated`) ở 45.000 yc/tháng và 5.784 đ (`0,48×`, `simulated`) khi khối lượng giảm một nửa.
- **Độ nhạy B1–B4:**
  - Xác nhận top 3 yếu tố ảnh hưởng mạnh nhất: **1. Số ca làm lại (+51,8%) · 2. Tỉ lệ xem lại (+40,7%) · 3. Lương nhân viên (+23,1%)** (`simulated`). Cặp giá token gấp đôi + xem lại gấp đôi cho 6.543 đ (+46,3%, `simulated`), khớp tính cộng tuyến tính.
  - B3 chứng minh giới hạn **2 lần chạy** rẻ nhất cho cả hệ thống (6.901.220 đ, `simulated`), khác với giới hạn có chi phí mỗi việc thành công thấp nhất là 1 lần (4.111 đ nhưng đẩy thêm 85 ca sang nhân viên, tổng hệ thống 7.449.781 đ, `simulated`).
  - B4 chứng minh xem lại 100% ở `noi_dia` + `hang_nang` làm chi phí tăng lên 11.743 đ (`0,98×`, `simulated`, với 9 phút làm lại) và 12.415 đ (`1,03×`, `simulated`, với trung bình dữ liệu 15,3 phút làm lại), mức hoà vốn xem lại lần lượt ≤ 5,1 phút và ≤ 4,8 phút.
- **Cỡ mẫu CP4 (D1):**
  - Tính đủ 5 câu D1: chia theo yêu cầu 1.251/nhóm (kiểm chứng `NormalIndPower`: 1.250); chia theo nhân viên với `m=75` cần DE = 2,48 → 3.103/nhóm (42 NV/nhóm, tổng 84 > 40); 20 NV/nhóm đạt tối đa 1.000 mẫu hiệu dụng; 6 depot/nhóm đạt tối đa 300.
  - Ở mức chênh 6 điểm (859/nhóm, `NormalIndPower`: 858) với 20 NV/nhóm cần `m >= 299` yêu cầu/NV (DE = 6,96), power thực ở mức chênh 5 điểm còn **0,64**.
  - Cung cấp tỉ lệ mở lại 7 ngày trong đợt chạy thử (4,25% toàn mẫu; 3,97% trong phạm vi pilot) và 3 chỉ số E1 (82,83% đóng 24h không mở lại; 27,12% bỏ qua gợi ý; 4,25% mở lại 7 ngày) để đồng bộ với các thành viên.

## 4. Bằng chứng

- Nhánh làm việc & PR: `feat/minh-phuong-lab13-core` (PR #1), `docs/team-and-group-report` (PR #7), review và đồng bộ chéo PR #1–#9 trên `main`.
- File mã nguồn hoàn chỉnh: `src/lab13.py` (chạy sạch bằng `cd src && ./venv/bin/python -W error lab13.py`, không có cảnh báo hay lỗi, in `Ba phép thử đáp án biết trước: ĐẠT` và đầy đủ bảng A1–A4, B1–B4, D1, E1).
- Bộ kiểm thử tự động: `tests/test_lab13.py` (14/14 unit & integration test đạt 100%).
- Hồ sơ tổng hợp & trình bày: `TEAM.md`, `report/team/group_report.md`, `report/team/phieu_cham.md` (chấm nhóm Delta), `docs/slide_gate2a_MoiNgayMotNhom.html`, và `report/team/2A202603997_NguyenMinhPhuong.md`.
- Bảo toàn nguyên trạng các file gốc (`src/lab13_starter.py`, `src/logix_runs.csv`, `src/logix_requests.csv`, `report/team/MSSV_HoTen.md`).

## 5. Công cụ AI đã dùng

- **Công cụ:** Antigravity (trợ lý lập trình AI).
- **Mục đích sử dụng:** Rà soát yêu cầu đề bài và kế hoạch phân công nhóm, viết khung kiểm thử `tests/test_lab13.py` theo quy trình TDD (đỏ → xanh), hoàn thiện cấu trúc hàm trong `src/lab13.py` và soát định dạng báo cáo cá nhân.
- **Cách tự kiểm tra kết quả:**
  - Chạy `src/venv/bin/python -m unittest discover -s tests -v` xác nhận 14/14 test vượt qua, bao gồm cả dữ liệu tổng hợp kiểm tra quy tắc "tử số tính mọi lần chạy, mẫu số chỉ đếm `thanh_cong`" và tính tuyến tính B1/B2.
  - Chạy `cd src && ./venv/bin/python -W error lab13.py` xác nhận chạy sạch không cảnh báo, 3 phép thử A1 in `ĐẠT` (`1,20 · 1,25 · 1,25`), và đối chiếu toàn bộ bảng A2, A3, A4, B1–B4, D1 với `docs/Lab13_Huong_dan_chi_tiet_buoi_chieu.md` (sai lệch < 0,1%, nhỏ hơn nhiều ngưỡng cho phép 2%).
  - Kiểm tra toàn bộ thư mục `report/` đảm bảo không chứa từ cấm theo quy tắc 5 của Lab 13 (chỉ dùng phạm vi pilot) và rà soát đầy đủ nhãn `simulated`.

## 6. Tự đánh giá

- Hoàn thành 100% đầu việc kỹ thuật và điều phối cho vai trò Team Lead & Core Dev: khoá sớm mã nguồn `src/lab13.py` và bộ test 14/14 PASS, review & đồng bộ số liệu chéo qua các PR #1–#9, dựng slide bảo vệ Gate 2a, hoàn thiện phiếu chấm nhóm Delta và rà soát đủ 5 quy tắc bắt buộc trên toàn bộ repository trước hạn nộp 23:59 GMT+7.
- Bài học rút ra: phân quyền sở hữu file ngay từ đầu giúp 4 thành viên làm song song không xung đột Git, nhưng vẫn cần một bước soát đồng bộ cuối cùng để chỉnh các sai lệch nhỏ về làm tròn, cách so sánh chi phí hệ thống và nhãn `simulated`.
