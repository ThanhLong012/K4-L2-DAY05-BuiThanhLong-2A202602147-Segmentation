# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602147
- Ngày / CVAT local: 17/9/2026
- Công cụ đã dùng: CVAT

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | submissions/easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | submissions/medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | submissions/hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | submissions/cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | submissions/cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | submissions/cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | submissions/cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | submissions/cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | submissions/cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000181542.jpg`, 1 xe máy ở nửa trái khung hình (nhóm xe máy gần người phụ nữ áo dài đang băng qua đường)
- Class và quy tắc tôi dùng để chọn biên: `motorcycle`; bám theo viền ngoài khung xe và bánh xe, tách riêng khỏi người đang ngồi lái (person là object khác) và không lấy phần bóng đổ trên mặt đường vào mask
- Nếu dùng gợi ý sau đó: không dùng gợi ý tự động (không có SAM/Intelligent Scissors trên CVAT lớp), toàn bộ vẽ tay bằng Brush/Polygon
- Nếu không dùng gợi ý: không dùng; quyết định gán nhãn: mỗi người lái và xe máy họ ngồi trên là 2 object riêng dù chồng lấn nhiều, vì instance segmentation yêu cầu tách theo vật thể chứ không theo vùng pixel liền khối

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance`, ảnh `000000181542.jpg`, khu vực nhóm người/xe máy băng qua đường
- Lỗi thuộc loại: gộp-tách
- Bằng chứng tôi nhìn thấy: khi kéo Brush liên tục qua nhiều vật cạnh nhau mà không kết thúc shape trước khi đổi vật, nhiều người/xe máy bị gộp chung vào 1 object; bảng Objects hiện ít dòng hơn hẳn số vật đếm được bằng mắt trên ảnh
- Quy tắc và hành động sửa: theo quy tắc "mỗi vật đếm được là một mask riêng" trong guideline-mini-sheet.md, tôi xoá các shape bị gộp rồi vẽ lại từng người/xe máy thành object riêng, kết thúc mỗi shape (double-click/chốt mask) trước khi bắt đầu vẽ vật tiếp theo
- Sau sửa đã Save và export lại chưa? Đã Save và export lại `medium_instance.zip`

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): chưa có điểm (ground truth chưa được phát). Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1 | `cp4_curb`, dải phân cách đất/cỏ ở giữa đường | (a) tính là road vì bề mặt là đất, không phải xi măng; (b) tính là sidewalk vì có bó vỉa bao quanh, chức năng phân cách/đi bộ | Theo quy tắc "ranh road–sidewalk theo chức năng và bó vỉa, không chỉ theo màu/vật liệu" | Quyết định: gán `sidewalk` cho dải phân cách vì có bó vỉa rõ, ưu tiên chức năng hơn vật liệu bề mặt |
| 2 | `easy_semantic`, ảnh `81ae7cbb-6bc63a4a.jpg`, các mảng cỏ/đất bị tuyết phủ | (a) vẫn tô `vegetation` vì biết bên dưới là cỏ; (b) để trống vì không chắc chắn nhìn thấy được bề mặt thật | Theo quy tắc "chỉ vẽ phần nhìn thấy, không tự đoán phần bị che" | Quyết định: những mảng tuyết phủ gần kín, không còn thấy rõ cỏ/đất bên dưới thì để trống, không ép vào `vegetation` |
| 3 | `cp6_coverage`, xe buýt và xe tải "CAPITAL" chiếm phần lớn khung hình | (a) gán tạm vào `car` vì gần giống nhất; (b) để trống vì `bus`/`truck` không có trong `classes.json` của task này | Theo quy tắc "tên lớp phải khớp classes.json của chính task, không dùng chung danh sách lớp của task khác" | Quyết định: để trống hoàn toàn phần xe buýt/xe tải, không gán nhầm vào `car` dù hình dáng có phần giống |
