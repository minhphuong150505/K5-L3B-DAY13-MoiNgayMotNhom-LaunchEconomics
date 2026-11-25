# Báo cáo nhóm

## 1. Thông tin nhóm

- **Tên nhóm:** `MoiNgayMotNhom`
- **Lớp:** `L3B`
- **Repository:** `K5-L3B-DAY13-MoiNgayMotNhom-LaunchEconomics`
- **Thành viên:** 4 thành viên (chi tiết vai trò và đóng góp xem [`TEAM.md`](../../TEAM.md))

## 2. Mục tiêu và cách tiếp cận

Nhóm dựng bộ **hồ sơ launch v0 (Gate 2a)** cho trợ lý hoàn phí giả định của **LogiX-VN** (12 depot, 40 nhân viên CSKH, 45.000 yêu cầu/tháng) dựa trên mẫu chạy thử 1.200 yêu cầu và 1.624 lần chạy (`src/logix_requests.csv`, `src/logix_runs.csv`) để trả lời bốn câu hỏi cốt lõi: chi phí thật mỗi việc thành công, mức độ sử dụng và hệ thống đo lường, quản trị lỗi, và thiết kế pilot tách được tác động.

Để chạy song song và tránh xung đột Git, nhóm áp dụng **phân quyền sở hữu file duy nhất** và tách hai luồng: Luồng A (Minh Phương, Hải Quân) khoá sớm mã nguồn `src/lab13.py`, đối chiếu số liệu A–B và cỡ mẫu D1; Luồng B (Ánh Dương, Việt Anh) gắn nhãn lỗi độc lập theo đúng `RULES.md`, thiết kế KPI/event và dựng hồ sơ Gate 2a. Toàn bộ PR được review chéo trước khi merge vào `main`.

## 3. Giải pháp

- **Nhiệm vụ A (CP1 · Mô hình chi phí):** Cài đặt 3 hàm kinh tế chạy lại và mô hình `mo_hinh(...)` trong [`src/lab13.py`](../../src/lab13.py) (kèm 14 unit/integration test trong [`tests/test_lab13.py`](../../tests/test_lab13.py)), kiểm số độc lập và trình bày bảng A1–A4 trong [`bang_chi_phi.md`](bang_chi_phi.md). Tử số tính mọi lần chạy (kể cả 572 lần lỗi), mẫu số chỉ đếm 978 việc `thanh_cong`.
- **Nhiệm vụ B (CP2 · Độ nhạy):** Chạy 9 kịch bản đơn yếu tố (B1), 1 kịch bản đổi cặp (B2), so sánh chi phí cả hệ thống cho giới hạn 1/2/3 lần chạy (B3) và kịch bản xem lại 100% ở phạm vi `noi_dia` + `hang_nang` (B4), ghi tại [`bang_chi_phi.md`](bang_chi_phi.md).
- **Nhiệm vụ C (CP3 · Bảng lỗi):** Hai người gắn nhãn (Ánh Dương, Việt Anh) gắn tay độc lập 20 ca theo 5 loại Google PAIR, giữ nguyên cột độc lập khi so nhãn, viết lại định nghĩa vì đồng thuận dưới 80%, thống nhất 8 ca lệch và xây dựng bảng khắc phục 5 ca (1, 2, 3, 11, 12) đo được bằng event và có 1 vai trò phụ trách tại [`bang_loi.md`](bang_loi.md).
- **Nhiệm vụ D (CP4 · Thiết kế pilot):** Tính đủ 5 câu cỡ mẫu D1 bằng công thức chuẩn và kiểm chứng chéo bằng `statsmodels.stats.power.NormalIndPower` trong [`src/lab13.py`](../../src/lab13.py), thiết kế thử nghiệm có đối chứng song song theo cụm nhân viên (`20 + 20`), chấp nhận mức chênh 6 điểm và đặt 4 luật dừng định lượng trong [`pilot_plan.yaml`](pilot_plan.yaml).
- **Nhiệm vụ E (CP5 · Chỉ số, rủi ro & Hồ sơ Gate 2a):** Tính thử 3 chỉ số, đề xuất 4 chỉ số bổ sung, thiết kế 10 event đều có `trace_id`, kiểm tra chéo chỉ số ↔ event và lập 4 dòng rủi ro kinh tế tại [`chi_so.md`](chi_so.md); tổng hợp thành hồ sơ một trang tại [`ho_so_launch_v0.md`](ho_so_launch_v0.md) và ghi nhận kết quả duyệt chéo tại [`phieu_cham.md`](phieu_cham.md).

## 4. Kết quả

- **Cổng A1 & Chi phí (A2–A4):** Vượt qua 3/3 phép thử A1 (`1,20 · 1,25 · 1,25`). Chi phí mỗi việc thành công đạt **4.472 đ** (`simulated`), gấp **16,3 lần** hoá đơn token + tool mỗi yêu cầu (274,7 đ); giờ nhân viên chiếm 92,5% tổng chi phí (làm lại 51,8%, xem lại 40,7% `simulated`). Tính cả 222 ca nhân viên làm thay, chi phí cả hệ thống là **5.865 đ/yêu cầu = 0,49×** của 12.000 đ (`simulated`). `quoc_te` không đáng chạy (**22.515 đ = 1,88×** `simulated`; tỉ lệ `ok` giảm 30,0% → 11,4% → 2,2%), `doi_tac` sát ngưỡng (**0,85×** `simulated`), nên thu hẹp pilot về `noi_dia` (0,22×) + `hang_nang` (0,69×). Cộng cố định 40 triệu đ/tháng: **4.599 đ = 0,38×** ở 45.000 yc/tháng và **5.784 đ = 0,48×** ở nửa khối lượng (`simulated`).
- **Độ nhạy (B1–B4):** Top 3 yếu tố nhạy nhất là **1. số ca làm lại (+51,8% / −25,9%) · 2. tỉ lệ xem lại (+40,7% / −20,3%) · 3. lương nhân viên (+23,1% khi tăng 25%)** (`simulated`). Cặp token ×2 + xem lại ×2 cho **6.543 đ (+46,3%)** (`simulated`). Giới hạn **2 lần chạy** rẻ nhất cho cả hệ thống (**6.901.220 đ** `simulated`, rẻ hơn 1 lần và 3 lần). Xem lại 100% ở phạm vi pilot tốn **11.743 đ = 0,98×** (9 phút làm lại) hoặc **12.415 đ = 1,03×** (15,3 phút trung bình dữ liệu `simulated`), mức hoà vốn xem lại lần lượt ≤ 5,1 phút và ≤ 4,8 phút.
- **Lỗi & Chỉ số (C, E1–E2):** Đồng thuận gắn nhãn độc lập đạt **12/20 = 60%**, nhóm đã viết lại định nghĩa trước khi thống nhất đủ 20/20 ca và hoàn thiện bảng khắc phục 5 ca. Chỉ số trong đợt chạy thử (chưa có đối chứng): đóng 24h không mở lại **82,83%** (994/1.200), bỏ qua gợi ý **27,12%** (48/177), mở lại 7 ngày **4,25%** toàn mẫu và **3,97%** trong phạm vi pilot (100% ca mở lại đều là ca `lam_lai`).
- **Cỡ mẫu (D1):** Chia theo yêu cầu cần **1.251/nhóm** (`NormalIndPower`: 1.250); chia theo nhân viên với `m = 75` cần 84 > 40 người; 20 nhân viên/nhóm có trần hiệu dụng **1.000**; 6 depot/nhóm có trần **300**. Chấp nhận mức chênh **6 điểm** (859/nhóm, `NormalIndPower`: 858) với 20 nhân viên/nhóm cần **m ≥ 299 yêu cầu/nhân viên** (`DE = 6,96`), đánh đổi power thực ở mức 5 điểm còn **0,64**.
- **Đề xuất & Duyệt chéo Gate 2a:** Nhóm chốt đề xuất **Go có điều kiện** trong [`ho_so_launch_v0.md`](ho_so_launch_v0.md) cho pilot phạm vi `noi_dia` + `hang_nang` (kèm bảng 4 điều kiện cụ thể: ký chấp nhận mức chênh 6 điểm / power 0,64, sửa khoá chống trùng và đối soát sổ cái ca 7 & 20, đo phút xem lại/làm lại thật thay số `simulated` sau tuần 1, và giảm xem lại theo bậc từ 100% ở bước 0.10 với ngưỡng hoà vốn ≤ 5,1 phút). Trong phiên duyệt chéo Gate 2a, nhóm chấm hồ sơ nhóm **Delta** đạt **25/30 điểm** với quyết định hội đồng **Go có điều kiện** (chi tiết tại [`phieu_cham.md`](phieu_cham.md)).

## 5. Khó khăn và cách xử lý

- **Đồng thuận gắn nhãn ban đầu dưới ngưỡng 80% (12/20 = 60%):** Hai người gắn nhãn nhầm giữa `Hệ thống` với `Giới hạn hệ thống` (ca 7, 13, 15, 20) và giữa `Ngầm` với các loại lỗi đã lộ ra (ca 6, 12, 17, 18). Nhóm giữ nguyên bộ nhãn độc lập theo `RULES.md`, viết lại định nghĩa phân biệt 2 cặp dễ lẫn rồi thống nhất 8 ca lệch (mở thêm PR #5 để chỉnh ca 12 thống nhất là `Ngầm`, khớp bảng khắc phục).
- **Lệch nhỏ khi đồng bộ đa file giữa 4 thành viên:** Khi review PR #2 và PR #3, nhóm phát hiện ký hiệu `±` chưa chuẩn ở B2 (`bang_chi_phi.md`), lệch 1 đ do làm tròn (`12.414` vs `12.415 đ`) và cách so sánh `0,37×` chưa cộng 222 ca chuyển nhân viên ở dòng lương +25% (`chi_so.md`). Cả ba điểm đã được sửa qua commit review trước khi đóng gói.
- **Mâu thuẫn cỡ mẫu và số cụm ở D1:** 40 nhân viên không đủ để phát hiện mức chênh 5 điểm khi chia theo cụm (`1.000 < 1.251`). Nhóm phân tích rõ đánh đổi và chọn chia theo nhân viên (`20 + 20`) ở mức chênh 6 điểm (`m ≥ 299`), ghi công khai con số bất lợi `power = 0,64` ở mức 5 điểm.

## 6. Tổng hợp đóng góp

Chi tiết vai trò, phần việc, đóng góp và bằng chứng commit/PR của cả 4 thành viên (Nguyễn Minh Phương, Nguyễn Văn Hải Quân, Nguyễn Ánh Dương, Trần Việt Anh) được ghi đầy đủ trong [`TEAM.md`](../../TEAM.md) và 4 file báo cáo cá nhân trong `report/team/`.

## 7. Hạn chế và hướng cải thiện

- **Dữ liệu thời gian nhân viên là giả lập:** 92,5% tổng chi phí (`xem_lai` + `lam_lai`) đến từ cột `_simulated`. Trong tuần 1 của pilot, phải đo thời gian thật qua `staff_review_decision.phut_xem_lai` và `staff_rework_completed.phut_lam_lai` rồi tính lại mô hình chi phí.
- **Đợt chạy thử không có nhóm đối chứng & power ở mức 5 điểm còn thấp (0,64):** Cần chạy pilot ngẫu nhiên phân tầng theo depot với nhóm đối chứng song song, và theo dõi chặt rủi ro tràn tác động (spillover) giữa nhân viên cùng depot bằng log theo `staff_id`.
- **Chưa giải quyết bài toán xem lại 100%:** Ở mức xem lại 100%, trợ lý gần như không tiết kiệm (`0,98–1,03×` `simulated`). Cần xây quy tắc giảm tỉ lệ xem lại theo bậc gắn với ngưỡng `sua + bo < 15%` và kiểm tra mẫu kế toán hằng tuần để bắt lỗi ngầm.

## 8. Tài liệu tham khảo

- Erol và cộng sự, *Cost-of-Pass: An Economic Framework for Evaluating Language Models*, [arxiv.org/abs/2504.13359](https://arxiv.org/abs/2504.13359).
- Google PAIR, *People + AI Guidebook*, chương "Errors + Graceful Failure", [pair.withgoogle.com](https://pair.withgoogle.com).
- Thư viện `statsmodels`, tài liệu `statsmodels.stats.power.NormalIndPower` và `proportion_effectsize`.
- Bộ tài liệu Lab 13 của môn học (`docs/du_lieu_va_cong_thuc.md`, `docs/Lab13_Huong_dan_chi_tiet_buoi_chieu.md`, `docs/Ngay13_Lab13_De_bai_hoc_vien.docx`).
