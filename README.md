
1. Mục tiêu bài Lab
--------------------
Bài thực hành này nhằm giúp em làm quen với thư viện PyTorch – 
một công cụ phổ biến trong học sâu (Deep Learning). 
Qua các bài tập, em được rèn luyện các kỹ năng cơ bản:
- Tạo và thao tác với Tensor.
- Thực hiện các phép toán, indexing, và reshape.
- Sử dụng cơ chế autograd để tính đạo hàm tự động.
- Hiểu rõ cách hoạt động của backward() và vấn đề khi gọi nhiều lần.
- Làm quen với các lớp cơ bản trong torch.nn như Linear, Embedding, và Module.
- Thực hiện một ví dụ huấn luyện đơn giản với mô hình nhỏ để quan sát quá trình lan truyền ngược (backpropagation).

2. Nội dung thực hiện
----------------------
Chương trình được chia thành ba phần chính:
- **Phần 1:** Tạo và thao tác với Tensor (Task 1.1 – 1.4).
- **Phần 2:** Tính toán gradient với autograd, minh họa cơ chế lưu và giải phóng đồ thị tính toán, 
  giải thích lý do gây lỗi khi gọi `z.backward()` nhiều lần, và cách khắc phục bằng `retain_graph=True` hoặc tái tính forward.
- **Phần 3:** Sử dụng mô-đun `torch.nn` để xây dựng mô hình cơ bản gồm `Linear`, `Embedding` và `SimpleModel` (kế thừa `nn.Module`).
  Ngoài ra, thực hiện một vòng huấn luyện thử nghiệm (training demo) trên dữ liệu giả lập nhằm minh họa quy trình huấn luyện:
  zero_grad() → forward → loss.backward() → optimizer.step().

3. Kết quả đạt được
--------------------
Chương trình chạy ổn định, cho ra kết quả đúng theo yêu cầu:
- Các phép toán Tensor và reshape hoạt động chính xác.
- Gradient tính được bằng autograd phù hợp với lý thuyết (`x.grad = 18`).
- Khi gọi backward() hai lần liên tiếp mà không giữ graph, PyTorch báo lỗi đúng như mong đợi.
- Khi sử dụng `retain_graph=True`, có thể backward nhiều lần và gradient được cộng dồn (`36` sau hai lần gọi).
- Các mô-đun Linear, Embedding, và mô hình SimpleModel chạy đúng, cho đầu ra hợp lệ.
- Training demo thực hiện thành công với giá trị loss hợp lý.
