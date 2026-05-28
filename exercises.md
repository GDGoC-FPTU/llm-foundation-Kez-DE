# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít thay đổi giữa các lần gọi. Khi tăng lên 0.5 và 1.0, câu trả lời tự nhiên hơn và có thể chọn các chi tiết khác nhau. Ở mức 1.5, nội dung đa dạng hơn nhưng rủi ro lan man hoặc chọn thông tin kém chắc chắn cũng cao hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2–0.4 cho chatbot hỗ trợ khách hàng. Use case này cần câu trả lời nhất quán, đúng chính sách và ít “sáng tạo” hơn so với chatbot giải trí hay brainstorming.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload có 10.000 × 3 × 350 = 10.500.000 output tokens/ngày. Với giá trong đề, GPT-4o tốn khoảng 10.500 × $0.010 = $105/ngày, còn GPT-4o-mini tốn khoảng 10.500 × $0.0006 = $6.30/ngày. Vì vậy GPT-4o đắt hơn khoảng 105 / 6.30 = 16.67 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o đáng dùng khi tác vụ cần reasoning tốt hơn, ví dụ phân tích hợp đồng, giải thích lỗi kỹ thuật phức tạp, hoặc tổng hợp tài liệu quan trọng. GPT-4o-mini phù hợp hơn cho workload lớn và lặp lại như FAQ chatbot, phân loại ticket, hoặc trả lời các câu hỏi ngắn đã có ngữ cảnh rõ.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần thấy hệ thống đang xử lý ngay, ví dụ chatbot, coding assistant, hoặc tác vụ giải thích nhiều bước. Nó giảm cảm giác chờ vì người dùng đọc được token đầu tiên trước khi toàn bộ câu trả lời hoàn tất. Non-streaming phù hợp hơn khi output ngắn, cần validate toàn bộ kết quả trước khi hiển thị, hoặc cần parse cấu trúc như JSON để tránh đưa ra dữ liệu chưa hoàn chỉnh.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
