# Team

## Thông tin nhóm

- **Tên nhóm:** `MoiNgayMotNhom`
- **Lớp:** `L3B`
- **Repo nhóm:** `K5-L3B-DAY13-MoiNgayMotNhom-LaunchEconomics`
- **URL repo:** https://github.com/minhphuong150505/K5-L3B-DAY13-MoiNgayMotNhom-LaunchEconomics
- **Nhánh nộp:** `main`
- **Trạng thái hoàn thiện:** Đã hoàn tất 5/5 checkpoint (CP1–CP5), hoàn chỉnh 6/6 file hồ sơ nhóm, 4/4 báo cáo cá nhân, duyệt chéo Gate 2a (chấm nhóm Delta đạt 25/30 — Go có điều kiện) và chốt trên nhánh `main` (PR #1–#9 và commit đóng gói cuối).

## Thành viên

| STT | Họ tên | MSSV | Email | GitHub | Vai trò |
| --: | ------ | ---- | ----- | ------ | ------- |
| 1 | Nguyễn Minh Phương | `2A202603997` | `phuongnm150505@gmail.com` | `@minhphuong150505` | Người viết code · Trưởng nhóm (Team Lead & Core Dev) |
| 2 | Nguyễn Văn Hải Quân | `2A202603994` | `nguyenhaiquan.data@gmail.com` | `@haiquanng` | Người viết code · Người kiểm số (Data & Stats Dev) |
| 3 | Nguyễn Ánh Dương | `2A202604087` | `anhduongn724@gmail.com` | `@nganhduong123` | Người gắn nhãn 1 (Error & Metrics Analyst) |
| 4 | Trần Việt Anh | `2A202604029` | `vietzanh04@gmail.com` | `@Vietzanh` | Người gắn nhãn 2, kiêm giữ hồ sơ (Gatekeeper) |

## Cá nhân

Bốn báo cáo cá nhân nằm trong `report/team/`:

- `report/team/2A202603997_NguyenMinhPhuong.md`
- `report/team/2A202603994_NguyenVanHaiQuan.md`
- `report/team/2A202604087_NguyenAnhDuong.md`
- `report/team/2A202604029_TranVietAnh.md`

---

## NguyenMinhPhuong-2A202603997

### Phần việc phụ trách

- Thiết lập repository nhóm `K5-L3B-DAY13-MoiNgayMotNhom-LaunchEconomics`, môi trường Python và quản lý phân nhánh, review/merge PR.
- Sở hữu và hoàn thiện toàn bộ mã nguồn `src/lab13.py` (CP1 A1–A4, CP2 B1–B4, CP4 D1 kèm kiểm chứng `statsmodels.stats.power.NormalIndPower`, và tham chiếu chỉ số đợt chạy thử E1/D3); giữ nguyên `src/lab13_starter.py` và 2 file CSV.
- Viết bộ kiểm thử tự động `tests/test_lab13.py` (14 test) và kiểm tra chất lượng chéo trước khi merge.

### Đóng góp cụ thể

- Vượt qua đủ 3 phép thử cổng A1 (`1,20 · 1,25 · 1,25`), xây dựng hàm `mo_hinh(...)` tính chi phí từ trace (4.472 đ/việc thành công `[simulated]`, gấp 16,3× hoá đơn 274,7 đ/yc; chi phí cả hệ thống 5.865 đ/yc = 0,49× `[simulated]`).
- Cài đặt đầy đủ phân tích theo loại A3, chi phí cố định A4 (4.599 đ = 0,38× ở 45.000 yc/tháng `[simulated]`), bảng độ nhạy B1–B2, tối ưu hệ thống B3 (giới hạn 2 lần rẻ nhất: 6.901.220 đ `[simulated]`), xem lại 100% B4 (11.743 đ và 12.415 đ `[simulated]`), và 5 câu cỡ mẫu D1 (`1.251 / 3.103 / 1.000 / 300 / 859`, `m >= 299`, power thực ở 5 điểm = `0,64`).
- Review các PR của thành viên và sửa trực tiếp so sánh công bằng `0,48×` ở dòng rủi ro lương +25% trong `report/team/chi_so.md`.

### Bằng chứng

- File: `src/lab13.py`, `tests/test_lab13.py`, `docs/slide_gate2a_MoiNgayMotNhom.html`, `TEAM.md`, `report/team/group_report.md`, `report/team/phieu_cham.md`, `report/team/2A202603997_NguyenMinhPhuong.md`.
- PR & commit: PR #1 (`bff4b9e`, merge `f0b6a06`), commit sửa đồng bộ `f2a86ea` (PR #2), PR #7 (`5718b24`, merge `aa60015`), slide trình bày (`d50140e`), rà soát & đóng gói chốt bài cuối phiên Gate 2a.
- Kiểm chứng: `src/venv/bin/python -m unittest discover -s tests -v` (14/14 PASS), `cd src && ./venv/bin/python -W error lab13.py` (0 lỗi, 0 cảnh báo).

---

## NguyenVanHaiQuan-2A202603994

### Phần việc phụ trách

- Sở hữu `report/team/bang_chi_phi.md` (hoàn thiện bảng A1–A4 và B1–B4).
- Kiểm số độc lập cho nhiệm vụ A và B, đối chiếu chéo với `src/lab13.py` của trưởng nhóm.
- Tính và kiểm chứng cỡ mẫu D1 bằng công thức và `statsmodels.NormalIndPower`, quy đổi thời lượng pilot bàn giao cho người giữ hồ sơ; soạn 4 dòng rủi ro kinh tế (E2) bàn giao cho người phụ trách `chi_so.md`.

### Đóng góp cụ thể

- Kiểm số độc lập toàn bộ A1–A4 và B1–B4, bổ sung bảng tỉ lệ `ok` theo lần thử ở A3 và độ nhạy 15,3 phút làm lại kèm ngưỡng hoà vốn xem lại (≤ 5,1 phút / ≤ 4,8 phút) ở B4 `[simulated]`.
- Đối chiếu D1 (`1.251 / 3.103 / 1.000 / 300 / 859`, `m = 299`, power = `0,64` ở 5 điểm, thời lượng pilot khoảng 4 tuần) và chuyển giao 4 dòng rủi ro kinh tế E2.
- Hỗ trợ rà soát và mở PR chốt thống nhất ca 12 là `Ngầm` trong `report/team/bang_loi.md` cho khớp bảng khắc phục.

### Bằng chứng

- File: `report/team/bang_chi_phi.md`, `report/team/2A202603994_NguyenVanHaiQuan.md` (hỗ trợ rà soát cuối ở `report/team/bang_loi.md` và `report/team/ho_so_launch_v0.md`).
- PR & commit: PR #3 (`89d52fb`, `225f2a2`, `5038743`, merge `5da7b54`), PR #5 (`f5d8e6d`, merge `82cc6ee`), hỗ trợ chốt PR #9 (`1d5d908`, merge `cde102b`).

---

## NguyenAnhDuong-2A202604087

### Phần việc phụ trách

- Sở hữu `report/team/bang_loi.md` (CP3 · Nhiệm vụ C): gắn nhãn độc lập 20 ca ở vai người gắn nhãn 1, thống kê tác động định lượng của lỗi từ CSV, xây dựng bảng khắc phục 5 ca đủ 5 loại Google PAIR.
- Sở hữu `report/team/chi_so.md` (CP5 · Nhiệm vụ E1, E2): tính thử 3 chỉ số, đề xuất chỉ số bổ sung, thiết kế danh sách event có `trace_id`, kiểm tra chéo và ghép 4 dòng rủi ro kinh tế từ Hải Quân.

### Đóng góp cụ thể

- Khai thác dữ liệu lỗi từ 2 file CSV: `572/1.624` lần lỗi (35,2%, 123.179 đ), `424` lần chạy lại (93.804 đ; `quoc_te` chiếm 49%), `148` ca chuyển nhân viên, `74` ca làm lại (51,8% tổng chi phí `[simulated]`), và phát hiện 51/51 ca mở lại trong 7 ngày đều là ca `lam_lai` (69%).
- Gắn nhãn tay độc lập 20 ca (khớp đáp án tham khảo 17/20, giữ nguyên cột độc lập theo `RULES.md`) và hoàn thiện bảng khắc phục 5 ca (1, 2, 3, 11, 12) có event, ngưỡng, tần suất và người phụ trách cụ thể.
- Hoàn thiện `chi_so.md`: 3 chỉ số tính thử (`82,83%`, `27,12%`, `4,25%`), 4 chỉ số tự đề xuất, 10 event có `trace_id`, kiểm tra chéo đầy đủ và 4 dòng rủi ro kinh tế E2.

### Bằng chứng

- File: `report/team/bang_loi.md`, `report/team/chi_so.md`, `report/team/2A202604087_NguyenAnhDuong.md`.
- PR & commit: PR #2 (`02d0f79`, `2f5d5a7`, merge `46dc4e0`).

---

## TranVietAnh-2A202604029

### Phần việc phụ trách

- Gắn nhãn độc lập 20 ca lỗi ở vai người gắn nhãn 2, so nhãn với Ánh Dương, thống nhất 8 ca lệch, viết quy tắc phân biệt và định nghĩa đã viết lại trong `report/team/bang_loi.md`.
- Giữ hồ sơ và Gatekeeper: tổng hợp `report/team/ho_so_launch_v0.md`, hoàn thiện `report/team/pilot_plan.yaml`, tổng hợp `report/team/phieu_cham.md` khi duyệt chéo Gate 2a, và soát 5 quy tắc bắt buộc của lab.

### Đóng góp cụ thể

- Gắn tay độc lập 20 ca lỗi (trùng 12/20 = 60% với người gắn nhãn 1); cùng Ánh Dương viết lại định nghĩa cho 2 cặp loại dễ nhầm (`Hệ thống / Giới hạn hệ thống` và `Ngầm / loại khác`), ghi 8 câu quy tắc phân biệt cho 8 ca lệch (`6, 7, 12, 13, 15, 17, 18, 20`) và hoàn thiện bảng thống nhất trong `bang_loi.md`.
- Hoàn thiện toàn bộ `report/team/pilot_plan.yaml` (đủ D1–D2, phân tích đánh đổi mức chênh 6 điểm, 4 luật dừng đủ 4 vế NẾU – TRONG – THÌ – KHÔNG THÌ, không còn dấu `?` và hợp lệ `yaml.safe_load`).
- Dựng và chốt toàn bộ 7 mục + đề xuất **Go có điều kiện** kèm bảng 4 điều kiện có ngưỡng, vai trò và ngày kiểm tra trong `report/team/ho_so_launch_v0.md`; tham gia duyệt chéo Gate 2a cùng nhóm.

### Bằng chứng

- File: `report/team/bang_loi.md`, `report/team/pilot_plan.yaml`, `report/team/ho_so_launch_v0.md`, `report/team/2A202604029_TranVietAnh.md`.
- PR & commit: `01e68ad` (`ho_so_launch_v0.md`), PR #4 (`38a0735`, `f041fe4`, `ba5585e`, merge `714e246`), PR #6 (`e793169`, merge `7da3b9e`), PR #8 (`3cf1285`, merge `bf44747`), PR #9 (`1d5d908`, merge `cde102b`).
