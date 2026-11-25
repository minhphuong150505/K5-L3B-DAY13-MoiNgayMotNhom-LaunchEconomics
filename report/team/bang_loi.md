# Bảng lỗi và cách khắc phục · Nhiệm vụ C

20 ca lỗi nằm trong `docs/Ngay13_Lab13_De_bai_hoc_vien.docx`. Năm loại theo Google PAIR: **Do người dùng · Hệ thống · Ngữ cảnh · Giới hạn hệ thống · Ngầm**. Gắn nhãn theo nguyên nhân gốc, không theo chỗ cần sửa.

## Hai bộ nhãn độc lập

Người gắn nhãn 1: Nguyễn Ánh Dương (Error & Metrics Analyst) · Người gắn nhãn 2: Trần Việt Anh (Gatekeeper, giữ hồ sơ) (gắn trong 8 phút, không trao đổi)

|  Ca | Nhãn người 1      | Nhãn người 2      | Trùng? | Nhãn thống nhất   |
| --: | ----------------- | ----------------- | ------ | ----------------- |
|   1 | Do người dùng     | Do người dùng     | Có     | Do người dùng     |
|   2 | Hệ thống          | Hệ thống          | Có     | Hệ thống          |
|   3 | Ngữ cảnh          | Ngữ cảnh          | Có     | Ngữ cảnh          |
|   4 | Giới hạn hệ thống | Giới hạn hệ thống | Có     | Giới hạn hệ thống |
|   5 | Ngầm              | Ngầm              | Có     | Ngầm              |
|   6 | Do người dùng     | Ngầm              | Không  | Do người dùng     |
|   7 | Giới hạn hệ thống | Hệ thống          | Không  | Hệ thống          |
|   8 | Hệ thống          | Hệ thống          | Có     | Hệ thống          |
|   9 | Do người dùng     | Do người dùng     | Có     | Do người dùng     |
|  10 | Ngữ cảnh          | Ngữ cảnh          | Có     | Ngữ cảnh          |
|  11 | Giới hạn hệ thống | Giới hạn hệ thống | Có     | Giới hạn hệ thống |
|  12 | Ngầm              | Hệ thống          | Không  | Ngầm              |
|  13 | Giới hạn hệ thống | Hệ thống          | Không  | Giới hạn hệ thống |
|  14 | Do người dùng     | Do người dùng     | Có     | Do người dùng     |
|  15 | Giới hạn hệ thống | Hệ thống          | Không  | Hệ thống          |
|  16 | Ngữ cảnh          | Ngữ cảnh          | Có     | Ngữ cảnh          |
|  17 | Ngầm              | Hệ thống          | Không  | Ngầm              |
|  18 | Ngữ cảnh          | Ngầm              | Không  | Ngữ cảnh          |
|  19 | Giới hạn hệ thống | Giới hạn hệ thống | Có     | Giới hạn hệ thống |
|  20 | Giới hạn hệ thống | Hệ thống          | Không  | Hệ thống          |

**Tỉ lệ đồng thuận:** 12 / 20 = 60%. Dưới ngưỡng 80% (16/20), nên nhóm đã viết lại định nghĩa (mục bên dưới) trước khi thống nhất 8 ca không trùng: 6, 7, 12, 13, 15, 17, 18, 20.

## Quy tắc phân biệt cho các ca không trùng

Mỗi ca không trùng một câu. Đồng thuận dưới 80% thì ghi định nghĩa đã viết lại.

- **Ca 6 → Do người dùng:** gốc lỗi là khách chọn mục "giao trễ" cho đơn hàng vỡ. Không phải Ngầm, vì khách bị từ chối và thấy ngay. Việc trợ lý nên đối chiếu mô tả với mục đã chọn ghi ở cột khắc phục.
- **Ca 7 → Hệ thống:** API sổ cái lỗi 503 là sự cố bên ngoài, nhưng trợ lý báo "đã hoàn tiền thành công" khi chưa ghi sổ là vi phạm thiết kế. Việc ghi sổ nằm trong phạm vi trợ lý, nên không phải Giới hạn.
- **Ca 12 → Ngầm:** kết quả hoàn tiền vẫn đúng, nhưng tiền token của depot D05 gấp 3 lần depot khác suốt 3 tuần mà không ai thấy. Sai ở đây là sai về chi phí và chỉ lộ ra khi kiểm tra, nên là Ngầm, không phải Hệ thống.
- **Ca 13 → Giới hạn hệ thống:** bảo hiểm hàng hoá là sản phẩm của đối tác, ngoài phạm vi trợ lý. Ngoài phạm vi thì là Giới hạn, kể cả khi trợ lý trả lời chung chung thay vì nói rõ.
- **Ca 15 → Hệ thống:** chính sách ghi trễ 24–48 giờ hoàn 50%, trợ lý tính 100%, tức là vi phạm chính sách. Trợ lý có đủ dữ liệu để tính đúng nên không phải Giới hạn, và nhân viên đã bắt được nên không phải Ngầm.
- **Ca 17 → Ngầm:** lệch 1.000–2.000 đ trên 212 đơn trong 9 ngày, không ai mở lại và không cảnh báo nào kích, chỉ lộ ra khi kiểm tra.
- **Ca 18 → Ngữ cảnh:** số tiền đúng chính sách (30.000 đ × 50% = 15.000 đ). Lỗi nằm ở giả định "khách hiểu cách tính". Không phải Ngầm, vì khách đã mở lại yêu cầu.
- **Ca 20 → Hệ thống:** hoàn hai lần vì lệnh thứ hai không có khoá chống trùng là thiếu sót thiết kế mà trợ lý phải xử lý được. Việc khách gửi lại sau 10 phút là hành vi bình thường, không làm lỗi thành Giới hạn hay Do người dùng.

Định nghĩa đã viết lại, dùng khi thống nhất nhãn (theo nguyên nhân gốc):

- **Do người dùng hay Hệ thống:** đầu vào của khách sai thì là Do người dùng, kể cả khi trợ lý xử lý kém; phần "trợ lý nên gợi ý" ghi ở cột khắc phục.
- **Hệ thống hay Ngầm:** sai đã lộ ra (khách mở lại, nhân viên bắt được, trích dẫn nhìn thấy) là Hệ thống; Ngầm chỉ khi 0 người nhận ra cho tới lúc kiểm tra mẫu.
- **Hệ thống hay Ngữ cảnh:** vi phạm thiết kế/chính sách là Hệ thống; làm đúng 100% thiết kế nhưng giả định lệch hoàn cảnh của khách là Ngữ cảnh.
- **Giới hạn hệ thống:** thiếu dữ liệu, ngoài phạm vi hoặc dạng đầu vào không đọc được thì là Giới hạn, kể cả khi trợ lý báo giới hạn đó kém.
- **Hệ thống hay Giới hạn hệ thống** (ca 7, 15, 20): việc nằm trong phạm vi trợ lý được thiết kế để làm (tính tiền, ghi sổ, chống trùng) mà làm sai là Hệ thống, kể cả khi nguyên nhân trực tiếp là một dịch vụ bên ngoài lỗi. Chỉ là Giới hạn khi trợ lý không thể làm được dù có cố.
- **Ngầm hay loại khác** (ca 6, 18): nếu khách đã phản ứng (bị từ chối, mở lại yêu cầu) thì lỗi đã lộ ra, không phải Ngầm. Khi đó xét tiếp theo nguyên nhân gốc: đầu vào của khách sai, hay giả định không khớp hoàn cảnh.

## Tác động định lượng của lỗi trong đợt chạy thử

Tính từ `src/logix_runs.csv` và `src/logix_requests.csv` (1.200 yêu cầu, 1.624 lần chạy).

| Dấu hiệu lỗi                              | Con số trong đợt chạy thử                                                          | Ý nghĩa cho bảng khắc phục                                                          |
| ----------------------------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Lần chạy lỗi (`status = loi`)             | 572/1.624 lần = 35,2%; tốn 123.179 đ token + tool                                  | Lần lỗi vẫn tốn tiền, nên tử số chi phí tính cả lần lỗi                             |
| Chạy lại (lần 2 và 3)                     | 424 lần, 93.804 đ; riêng quoc_te 198 lần, 46.218 đ (49%)                           | quoc_te lần 1 ok 30%, lần 2 11,4%, lần 3 2,2%: chạy lại không cứu được lỗi Giới hạn |
| Chuyển nhân viên (`chuyen_nhan_vien`)     | 148 ca = 12,3%; 91 ca quoc_te, 23 doi_tac                                          | Nhân viên làm thay 148 × 12.000 đ = 1.776.000 đ                                     |
| Làm lại (`lam_lai`)                       | 74 ca = 6,2%; 1.132 phút = 2.264.000 đ [simulated], 51,8% tổng chi phí [simulated] | Khoản chi phí lớn nhất, nên lỗi Hệ thống là ưu tiên sửa số 1                        |
| Lỗi lọt đến khách (`mo_lai_trong_7_ngay`) | 51/1.200 = 4,25%; cả 51 ca đều là `lam_lai` (69% số ca làm lại)                    | Trong phạm vi noi_dia + hang_nang là 3,97% (39/982): mốc cho luật dừng an toàn      |

## Bảng khắc phục cho 5 ca, mỗi loại một ca

Cách phát hiện phải đo được (event, ngưỡng, tần suất). Người phụ trách là một vai trò cụ thể.

|  Ca | Loại lỗi          | Phát hiện bằng gì                                                                                                                                                              | Khắc phục thế nào                                                                                                                                                   | Ai phụ trách       |
| --: | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
|   1 | Do người dùng     | Event `refund_ledger_write` có `ket_qua = bank_rejected` theo `trace_id`; cảnh báo khi quá 1% số yêu cầu/ngày (khoảng 15/1.500)                                                | Kiểm tra độ dài số tài khoản theo ngân hàng và hiện tên chủ tài khoản cho khách xác nhận trước khi tạo lệnh; ngân hàng từ chối thì mời khách sửa, không đóng ticket | PM trợ lý hoàn phí |
|   2 | Hệ thống          | Kiểm tra mỗi ngày: lần gọi tool tra giá có `loai_hang = thuong` trong khi vận đơn ghi hàng nặng (28 kg); ngưỡng 0 ca; kèm `ticket_reopened` có `reason = hoan_thieu` theo tuần | Agent lấy loại hàng và cân nặng từ dữ liệu vận đơn, không tự suy; chặn gọi tool khi tham số lệch vận đơn; đối soát số tiền hoàn với bảng giá trước khi gửi          | Kỹ sư trưởng agent |
|   3 | Ngữ cảnh          | Event `ticket_reopened` có `reason = chua_nhan_tien` trong khi sổ cái đã ghi ok về ví; theo tuần, cảnh báo khi quá 0,5% số yêu cầu                                             | Hỏi khách chọn nhận về ví (5 phút) hay ngân hàng (1–3 ngày) trước khi hoàn; tin nhắn luôn ghi kênh nhận và thời gian tiền về                                        | Trưởng nhóm CSKH   |
|  11 | Giới hạn hệ thống | Event `handoff_to_staff` có `reason = dau_vao_khong_ho_tro` (âm thanh), đếm theo tuần; quá 2% số yêu cầu thì đưa xử lý thoại vào lộ trình                                      | Nói rõ "chưa nghe được tin nhắn thoại", đưa 3 nút lý do hoàn phổ biến và ô gõ chữ; khách vẫn cần thoại thì chuyển nhân viên kèm file, không cụt đường               | PM trợ lý hoàn phí |
|  12 | Ngầm              | Báo cáo tuần chi phí token + tool mỗi yêu cầu theo depot từ `agent_run_completed`; cảnh báo khi một depot > 1,5× trung vị (đợt chạy thử: 259–287 đ/yêu cầu, chênh tối đa 11%)  | Tool tra đơn kiểm tra đủ trường và trả lỗi rõ thay vì để agent gọi lại; ghi `depot` và số lần gọi tool vào trace để chia nhỏ chi phí                                | Kỹ sư trưởng agent |
