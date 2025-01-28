---
Creation_date: 2022-07-24 13:33
Modification_date: Sunday 24th July 2022 13:33:31
Indexes:
  - "[[selenium]]"
---

----


> Things do not change; we change.
> — <cite>Henry David Thoreau</cite>


**Hard Assert**

Trong trường hợp một test case mà có nhiều steps thì khi mà Hard Assert failed ở step nào nó ở chính giữa test case thì toàn bộ test case sẽ không chạy tiếp nữa.
* **Best Pratice**
	* Hàm trả về có kiểu dữ liệu là boolean thì tốt nhất là sử dụng assertTrue/False
	* Hàm trả về text thì tốt nhất sử dụng assertEqual
* **Ưu điểm**
	* Có kết quả nhanh
	* Phù hợp với các level: Unit/ API testing
* **Nhược điểm**
	* Phải run lại nhiều lần để chạy qua hết all test cases/ steps hoặc phải manual test lại nhiều step/ case
	* Không phù hợp với UI testing


**Verify (Custom Hard Assert)**

Verify thì có thể chạy tiếp nếu như có một step bất kỳ bị fail
* **Ưu điểm**
	* Chạy qua hết all test cases/ steps, tới khi có kết quả thì sẽ biết được có bao nhiêu steps bị fail.
	* Phù hợp với UI/ E2E testing
* **Ngược điểm**
	* Có kết quả chậm do phải đợi chạy hết trong một lần
