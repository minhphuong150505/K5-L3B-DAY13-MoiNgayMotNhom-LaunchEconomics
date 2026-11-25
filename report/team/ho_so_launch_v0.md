# Hồ sơ launch v0 · Trợ lý hoàn phí LogiX-VN · Gate 2a

Nhóm: MoiNgayMotNhom · Lớp: L3B · Gate 2a duyệt kế hoạch pilot, chưa phải duyệt chạy chính thức. Số từ cột `_simulated` ghi nhãn [simulated].

| Mục | Con số chính | Trạng thái | Người phụ trách |
| --- | --- | --- | --- |
| 1 · Chi phí mỗi việc thành công | **4.472 đ** (978/1.200 yêu cầu), gấp **16,3 lần** hoá đơn token + tool 274,7 đ/yêu cầu. Giờ nhân viên chiếm 92,5% (làm lại 51,8%, xem lại 40,7%). Trong phạm vi noi_dia + hang_nang: 3.414 đ [simulated] | Giả lập | PM trợ lý hoàn phí |
| 2 · Ba yếu tố nhạy nhất | 1. Số ca làm lại: +51,8% / −25,9% · 2. Tỉ lệ xem lại: +40,7% / −20,3% · 3. Lương nhân viên: +23,1% khi tăng 25%. Giá token gấp đôi chỉ +5,6% [simulated] | Giả lập | Trưởng nhóm CSKH |
| 3 · So với nhân viên tự làm (12.000 đ) | Phạm vi pilot, đã cộng cố định 40 triệu đ/tháng: **4.599 đ = 0,38×** (45.000 yêu cầu/tháng), 5.784 đ = 0,48× ở nửa khối lượng. Cả hệ thống, tính 222 ca nhân viên làm thay: 5.865 đ = 0,49×. Bất lợi: quoc_te **1,88×**, doi_tac 0,85× nên loại khỏi pilot; xem lại 100% thì **0,98–1,03×** [simulated] | Giả lập | Giám đốc vận hành |
| 4 · Chỉ số chính, dùng, an toàn | Trong đợt chạy thử (chưa có đối chứng): chính 82,83% (994/1.200) · bỏ qua gợi ý 27,12% (48/177) · mở lại trong 7 ngày 4,25% (51/1.200), trong phạm vi 3,97%. 10 event đều có `trace_id`, mọi chỉ số tính được từ event (`chi_so.md`) | Xong, có bằng chứng | PM trợ lý hoàn phí |
| 5 · Bảng lỗi và cách khắc phục | Đồng thuận độc lập **12/20 = 60%** (dưới 80%), đã viết lại định nghĩa và thống nhất 8 ca lệch. Bảng khắc phục 5 ca (1, 2, 3, 11, 12) đủ 5 loại, mỗi ca có event, ngưỡng và một vai trò phụ trách (`bang_loi.md`) | Xong, có bằng chứng | Kỹ sư trưởng agent |
| 6 · Pilot plan | Chia theo nhân viên 20 + 20, ngẫu nhiên phân tầng theo depot, đối chứng song song. Mức chênh **6 điểm** (859/nhóm, m ≥ 299, DE 6,96); ở mức 5 điểm power chỉ **0,64**. 4 luật dừng đủ 4 vế, trần an toàn 6%. Bắt đầu 2026-12-07, quyết định 2027-01-11 (`pilot_plan.yaml`) | Xong, có bằng chứng | Giám đốc vận hành |
| 7 · Rủi ro kinh tế | Làm lại gấp đôi: 6.787 đ (+51,8%) · xem lại 100%: 11.743 đ = 0,98× (12.415 đ = 1,03× với 15,3 phút làm lại) · khối lượng còn một nửa: cố định +2.370 đ/việc · lương +25%: 7.262 đ = 0,48× của 15.000 đ (`chi_so.md`) [simulated] | Giả lập | PM trợ lý hoàn phí |

**Đề xuất: Go có điều kiện**, chỉ cho pilot noi_dia + hang_nang (4.599 đ = 0,38× đã cộng cố định [simulated]). Con số bất lợi: xem lại 100% thì 11.743 đ = 0,98× [simulated], và pilot chỉ đủ power cho mức chênh 6 điểm (0,64 ở 5 điểm). Các điều kiện:

| Điều kiện | Ngưỡng / bằng chứng | Người phụ trách | Ngày kiểm tra |
| --- | --- | --- | --- |
| Ký chấp nhận mức chênh 6 điểm | Văn bản chấp nhận power 0,64 ở mức 5 điểm | Giám đốc vận hành | 2026-12-04 |
| Sửa khoá chống trùng và đối soát sổ cái (ca 7, 20) | 0 ca hoàn trùng trong kiểm thử 100 đơn | Kỹ sư trưởng agent | 2026-12-04 |
| Đo phút xem lại và làm lại thật thay số simulated | Event `staff_review_decision`, `staff_rework_completed` đủ `trace_id`; tính lại chi phí | PM trợ lý hoàn phí | 2026-12-14 (hết tuần 1) |
| Giảm xem lại theo bậc, từ 100% ở bước 0.10 | Chỉ giảm khi sửa + bỏ < 15% trong 1 tuần; mỗi lần xem lại ≤ 5,1 phút (hoà vốn B4) | Trưởng nhóm CSKH | 2026-12-21 (hết tuần 2) |
