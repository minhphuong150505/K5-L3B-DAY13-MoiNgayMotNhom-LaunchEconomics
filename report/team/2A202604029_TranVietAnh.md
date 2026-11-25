# Báo cáo cá nhân — TranVietAnh-2A202604029

## 1. Thông tin thành viên

- Họ tên: Trần Việt Anh
- MSSV: 2A202604029
- Email: <vietzanh04@gmail.com>
- Vai trong nhóm (người viết code, người kiểm số, người gắn nhãn 1, người gắn nhãn 2 kiêm giữ hồ sơ): người gắn nhãn 2 kiêm giữ hồ sơ · Gatekeeper

## 2. Phần việc phụ trách

- CP3 · Nhiệm vụ C: gắn nhãn độc lập 20 ca với vai người gắn nhãn 2, so nhãn với Nguyễn Ánh Dương (người gắn nhãn 1), thống nhất 8 ca lệch, viết quy tắc phân biệt và định nghĩa đã viết lại trong `report/team/bang_loi.md`.
- CP5 · Nhiệm vụ E3: giữ `report/team/ho_so_launch_v0.md`, điền dần từ đầu buổi theo kết quả các CP; chốt đề xuất cuối cùng cùng nhóm.
- Duyệt chéo Gate 2a: gửi hồ sơ cho nhóm hội đồng, trình bày hồ sơ 1 phút và trả lời câu hỏi của hội đồng.

## 3. Đóng góp cụ thể

- Gắn nhãn tay 20 ca lỗi, độc lập và không trao đổi với người gắn nhãn 1. Khi so nhãn: trùng 12/20 = 60%, dưới ngưỡng 80%.
- Cùng người gắn nhãn 1 thống nhất nhãn cho 8 ca lệch (6, 7, 12, 13, 15, 17, 18, 20). Mỗi ca ghi một câu quy tắc phân biệt. Vì đồng thuận dưới 80%, bổ sung định nghĩa đã viết lại cho hai cặp loại hay bị lẫn: Hệ thống / Giới hạn hệ thống và Ngầm / loại khác.
- Điền cột Trùng?, nhãn thống nhất cho 12 ca trùng và tỉ lệ đồng thuận trong `bang_loi.md`.
- Hồ sơ launch v0: điền mục 1–3 từ `bang_chi_phi.md`:
  - chi phí mỗi việc thành công 4.472 đ, gấp 16,3 lần hoá đơn token chia số yêu cầu [simulated];
  - ba yếu tố nhạy nhất: làm lại +51,8%, xem lại +40,7%, lương +23,1% [simulated];
  - so với nhân viên tự làm: phạm vi pilot đã cộng chi phí cố định 4.599 đ = 0,38×, nhưng xem lại 100% thì 0,98–1,03× [simulated].
- Hoàn thiện toàn bộ `report/team/pilot_plan.yaml` (D1, D2, đánh đổi mức chênh 6 điểm, 4 luật dừng đủ 4 vế, không còn dấu `?`).
- Hoàn thiện đủ 7 mục và chốt đề xuất **Go có điều kiện** kèm bảng 4 điều kiện có ngưỡng, người phụ trách và ngày kiểm tra trong `report/team/ho_so_launch_v0.md`.

## 4. Bằng chứng

- `report/team/bang_loi.md`: cột Nhãn người 2, cột Trùng?, cột Nhãn thống nhất, tỉ lệ đồng thuận, quy tắc cho 8 ca lệch, định nghĩa đã viết lại.
- `report/team/pilot_plan.yaml`: kế hoạch pilot đầy đủ, hợp lệ `yaml.safe_load`.
- `report/team/ho_so_launch_v0.md`: bảng 7 mục và đề xuất **Go có điều kiện** kèm 4 điều kiện.
- Commit & PR:
  - `01e68ad`: dựng khung hồ sơ launch v0;
  - PR #4 (`38a0735`, `f041fe4`, `ba5585e`): cột Nhãn người 2, Nhãn thống nhất và hoàn thiện bảng lỗi;
  - PR #8 (`3cf1285`): điền hoàn chỉnh `pilot_plan.yaml`;
  - PR #9 (`1d5d908`): chốt hồ sơ launch v0 (Go có điều kiện).

## 5. Công cụ AI đã dùng

- Claude Code dùng vào các việc sau:
  - đọc đề và giải thích yêu cầu từng CP, vai trò và cách chấm;
  - đối chiếu số trong `bang_chi_phi.md` với output của `src/lab13.py`;
  - soạn nháp hồ sơ launch mục 1–3 từ `bang_chi_phi.md`;
  - tạo nhánh git và chép bộ nhãn của tôi vào bảng mới nhất trên `main`;
  - soạn nháp cột Trùng?, tỉ lệ đồng thuận, câu quy tắc cho các ca lệch theo nhãn nhóm đã chốt, và định nghĩa đã viết lại.
- Không dùng AI để gắn nhãn. Tôi đã yêu cầu AI điền nhãn người 2 và AI từ chối theo `RULES.md`. 20 nhãn của tôi được gắn tay, độc lập, trước khi so. Nhãn thống nhất của 8 ca lệch do hai người gắn nhãn tự quyết.
- Tự kiểm tra:
  - mọi số trong hồ sơ mục 1–3 được đối chiếu với `bang_chi_phi.md` và output `python lab13.py` (4.472 đ, 16,3 lần, 4.599 đ, 0,38×, 11.743 đ);
  - tỉ lệ đồng thuận được đếm lại thủ công trên bảng (12/20);
  - đọc lại từng câu quy tắc với mô tả ca trong `docs/Ngay13_Lab13_De_bai_hoc_vien.docx`.

## 6. Tự đánh giá

- Làm tốt: hồ sơ được điền từ sớm theo đúng vai giữ hồ sơ; mọi số giả lập có nhãn [simulated]; mục chưa có bằng chứng ghi "Chưa" thay vì điền số chưa kiểm chứng.
- Cần cải thiện:
  - Sau khi so với nhãn tham khảo, bộ nhãn của tôi khớp 15/20 (lệch ca 6, 12, 13, 17, 18). Tôi gắn "Hệ thống" quá rộng và chưa phân biệt rõ Ngầm với lỗi đã lộ ra.
  - Bài học 1: Ngầm chỉ khi không ai nhận ra cho tới lúc kiểm tra mẫu. Khách đã mở lại hay đã bị từ chối thì lỗi đã lộ ra.
  - Bài học 2: ngoài phạm vi trợ lý thì là Giới hạn hệ thống, kể cả khi trợ lý trả lời kém.
- Cập nhật hoàn tất các đầu việc tồn đọng trước đó:
  - đã thống nhất ca 12 là `Ngầm` trong `bang_loi.md` (PR #5) cho khớp bảng khắc phục;
  - đã hoàn thiện `pilot_plan.yaml` (PR #8) và chốt đủ mục 4–7 cùng đề xuất **Go có điều kiện** trong `ho_so_launch_v0.md` (PR #9).
