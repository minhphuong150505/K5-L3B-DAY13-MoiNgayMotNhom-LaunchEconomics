# Phiếu chấm hội đồng Gate 2a

Nhóm số n chấm nhóm số n + 1; nhóm cuối chấm nhóm 1. Chấm theo bằng chứng trong hồ sơ, không theo cách trình bày: một đề xuất No-go có lý do bằng số được điểm cao hơn một đề xuất Go bỏ qua con số bất lợi.

- Nhóm chấm (hội đồng): MoiNgayMotNhom (L3B)
- Nhóm được chấm: Delta (L3B)

| Tiêu chí | 0 điểm | 5 điểm | 10 điểm | Điểm | Lý do (có số) |
| --- | --- | --- | --- | ---: | --- |
| Đề xuất khớp bằng chứng | Mâu thuẫn với số của chính nhóm | Khớp nhưng bỏ qua một con số bất lợi | Khớp, nêu cả con số bất lợi và cách xử lý | 10 | Đề xuất **Go có điều kiện** khớp bằng chứng chi phí (phạm vi `noi_dia` + `hang_nang` đạt khoảng 0,38× mức 12.000 đ [simulated]), có nêu con số bất lợi (xem lại 100% sát 12.000 đ, power ở 5 điểm dưới 0,8) và điều kiện xử lý. |
| Số giả lập và phạm vi | Không nhãn; phạm vi "mọi yêu cầu" | Có nhãn hoặc có thu hẹp phạm vi | Nhãn ở mọi số giả lập; phạm vi thu hẹp có lý do bằng số | 5 | Đã thu hẹp phạm vi khỏi nhóm lỗ (`quoc_te` 1,88× [simulated]) và có đánh dấu nguồn giả lập, nhưng trình bày còn thiếu một vài chỗ về nhãn `simulated` nhất quán và chưa bổ sung ngưỡng trần số tiền/giá trị đơn trong phạm vi pilot. |
| Pilot ra được quyết định | Không đối chứng hoặc thiếu cỡ mẫu | Đủ cỡ mẫu, luật dừng chung chung | Tách được tác động, đủ mẫu, luật dừng có ngưỡng, thời hạn, người có quyền dừng | 10 | Có nhóm đối chứng song song, phân tích rõ cỡ mẫu cụm (20 cụm/nhóm) và đủ 3 nhóm luật dừng (an toàn, chi phí, mức độ sử dụng) kèm ngưỡng định lượng, thời hạn và người có quyền dừng. |
| **Tổng** | | | | **25 / 30** | Đạt 25/30 theo thang 0–5–10; trình bày khá kỹ nhưng còn thiếu một vài chi tiết ở tiêu chí 2. |

**Quyết định của hội đồng:** Go có điều kiện

**Lý do:** Hồ sơ của nhóm Delta trình bày khá kỹ về mô hình chi phí và thiết kế pilot (25/30 điểm), nhưng trước khi chạy pilot cần rà soát bổ sung đủ nhãn `simulated` ở mọi con số tính từ cột `_simulated`, làm rõ giới hạn phạm vi đối với các đơn có giá trị lớn và phương án ứng phó khi số tiền/chi phí phát sinh tăng gấp 3 lần.

**Một câu hỏi cho đội trình:** Nếu số tiền hoàn phí hoặc chi phí phát sinh thực tế lớn hơn gấp 3 lần so với mức hiện tại thì nhóm sẽ xử lý như thế nào?

**Câu trả lời của đội trình (ghi lại tại buổi):** Đội trình nêu hướng kích hoạt luật dừng chi phí, tạm dừng mở rộng rollout, tách các đơn giá trị lớn chuyển thẳng cho nhân viên xử lý và rà soát trace nguyên nhân trước khi bật lại trợ lý. Hội đồng ghi nhận hướng xử lý phù hợp và yêu cầu đưa thêm ngưỡng trần giá trị đơn vào điều kiện trước pilot.
