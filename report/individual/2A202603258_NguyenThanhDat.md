# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603258
- Ngày / CVAT local: 12/11/2026
- Công cụ đã dùng: cvat local

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task            | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --------------- | ----------------- | -----------------: | ---------------------------: |
| easy_semantic   | easy_semantic     |              3 / 3 |                           20 |
| medium_instance | medium_instance   |              3 / 3 |                           32 |
| hard_panoptic   | hard_panoptic     |              2 / 2 |                           30 |
| cp1_holes       | cp1_holes         |              1 / 1 |                            3 |
| cp2_slice       | cp2_slice         |              1 / 1 |                            3 |
| cp5_occlusion   | cp5_occlusion     |              1 / 1 |                            3 |
| cp3_thin        | cp3_thin          |              1 / 1 |                            3 |
| cp4_curb        | cp4_curb          |              1 / 1 |                            3 |
| cp6_coverage    | cp6_coverage      |              1 / 1 |                            3 |
| **Tổng tối đa** |                   |                    |                      **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: ảnh 000000373353.jpg, vị trí giữa ảnh và object là person
- Class và quy tắc tôi dùng để chọn biên: class person và quy tắc Vẽ sát **phần nhìn thấy**, không tự đoán phần bị che.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: vùng gợi ý lệch, hành động sửa lại để khoanh đúng phần biên của vật
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: medium_semantic / 000000373353.jpg / biên xe ở giữa
- Lỗi thuộc loại: biên, sai lớp.
- Bằng chứng tôi nhìn thấy: mask person che lấp phần lớp car.
- Quy tắc và hành động sửa: xác định ranh theo bó vỉa và chức năng;
  vẽ phần car qua phần người, không vẽ qua người.
- Sau sửa đã Save và export lại chưa? Đã Save, xuất lại
  COCO 1.0 và thay submissions/medium_semantic.zip.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): chưa chạy đánh giá, chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí       | Hai cách hiểu có thể                    | Quy tắc/chứng cứ                 | Quyết định hoặc câu hỏi cho coach                                                             |
| ---------------- | --------------------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------- |
| 000000373353.jpg | Xe car bị cắt đôi bởi người đi đường    | người đi đường chắn ngang xe car | Không biết nên chia thành hai vật thể hay vẫn vẽ luôn cả phần bị chia cắt để thành 1 vật thể? |
| 000000458325.jpg | ảnh person có pixel mờ vì trị trí xa    | pixel bị mờ                      | Không phân biệt được đâu là vật thể với các vật thể còn lại                                   |
| 000000144300.jpg | ảnh person bị chia cắt bởi vật thể khác | xe motor chia cắt person         | vẫn vẽ phần chiếm nhiều phần trăm nhất của vật thể                                            |
