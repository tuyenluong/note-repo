**Về kiến thức Selenium**
* Selenium là gì?
	* Selenium là một bộ công cụ để kiểm tra web tự động. Nó gồm có 3 thành phần: Selenium IDE, WebDriver và RC, Grid
* Làm cách nào tìm element với Selenium?
	* Mình có thể tìm elements với method như findElement hoặc findElements số nhiều. Với 2 cách trên thì có thể tìm Locator với nhiều cách khác nhau như:
		* ID, Name, Class, Tag, Attribute, CSS, Linktext, Linktext 1 phần, Xpath
* Anh/Chị thấy em có đề cập tới X-path, vậy thì công dụng của nó là gì?
	* Xpath được sử dụng để tìm element trên web page, nhưng nó cũng có hữu dụng trong việc sử dụng cho Dynamic elements
* Và trong X-path, sự khác biệt giữa 1 dấu "/" và 2 dấu "//" là gì?
	* Dấu gạch chéo đơn được sử dụng để tạo XPath tuyệt đối trong khi dấu gạch chéo kép được sử dụng để tạo XPath tương đối.
* Preceding and Following trong axe xpath là gì?
	* Preceding là phía trước của 1 thẻ nhưng ko phải là cha mẹ tổ tiên.
	* Following là phía sau của 1 thẻ nhưng ko phải là con cháu chắt.
* Dynamic Elements là gì?
	* Dạ là sự kết hợp giữa String format trong Java và Xpath ạ.
* Những loại test được supported bởi Selenium?
	* Functional testing và Regression Testing (Đáng lẽ Regression testing đã nằm trong Functional testing rồi nhưng do Regresstion chủ yếu được test bởi automation nên mới dc nhắc tới.)
* Assertions là gì? Và có bao nhiêu loại Assertions?
	* Assertions là phương thức để xác minh rằng trạng thái của ứng dụng đó khớp với những gì dc mong đợi. Những loại Assertions đó là Assert, Verify, waitFor
*  Sự khác biệt giữa Verify và Assertions?
	* Assert sẽ kiểm tra xem có element trong webpage hay không. Nếu không tìm dc element thì nó sẽ dừng tại test case đó.
	* Verify thì cũng như Assert là sẽ kiểm tra xem có element có trong page hay không, nhưng khác chỗ là nếu thằng Verify không tìm dc thì test vẫn chạy như bình thuòng.
* Những khó khăn về technial với Selenium?
	* Chỉ support trên web app
	* Không có khả năng tạo report, phải sử dụng các tools khác kết hợp
	* Và vì là open source nên sẽ ko có technical support thực sự đáng tin cậy, và các features mới cũng sẽ ko hoạt động dc ổn định.
* TestNg là gì?
	* TestNG là một testing framework dành cho ngôn ngữ JAVA. Mục tiêu thiết kế của TestNG là bao phủ nhiều loại categories test khác nhau như: unit, functional, end-to-end, integration, etc., 
	* Các chức năng chính của TestNG:
		* Có nhiều loại annotation After và Before
		* Tính năng Run test phụ thuộc (ví dụ điều kiện run B là bắt buộc run A trước)
		* Có khả năng group các test methods
		* Chạy Multithread
		- Report bằng HTML
* TestNG Annotations là gì? Sự khác biệt giữa các Annotations được sử dụng?
	* After và Before được sử dụng khi cần set up môi trường trước khi test và clear mọi thứ sau khi đã xong
	* After và Before có nhiều level khác nhau để set up (*Được xếp theo thứ tự cao tới thấp*):
		*  @BeforeSuite
		-   @BeforeTest
		-   @BeforeClass
		-   @BeforeMethod
		-   @Test
		-   @AfterMethod
		-   @AfterClass
		-   @AfterTest
		-   @AfterSuite
* Các loại wait dc hỗ trợ bởi Selenium? 
	* Implicit wait (Đợi ngầm) sẽ đợi một khoản thời gian nhất định trước khi tìm element và cho ra error No Such Element
	* Explicit wait ngoài đợi theo một khoản thời gian ra thì còn có thể đợi theo các điều kiện tương ứng rồi mới cho ra error ElementNotVisibleException
	* Fluent wait
* Lúc sử dụng lệnh click, thì có thể sử dụng tọa độ của màn hình để định vị ko?
* Những lợi thế của Selenium?


**Về kiến thức lập trình**
* Sự khác biệt giữa JDK và JRE là gì?
	* **JDK (Java Development Kit- Bộ công cụ phát triển Java)** là một bộ công cụ phát triển phần mềm để phát triển các ứng dụng trong Java
		* Khi bạn tải JDK, JRE cũng được tải xuống và không cần phải tải xuống riêng. Ngoài JRE, JDK cũng chứa một lượng công cụ phát triển (trình biên dịch, JavaDoc, Trình gỡ lỗi Java, v.v.).
	* **JRE ( Java Runtime Environment)** là gói phần mềm cung cấp các thư viện lớp Java, cùng với Máy ảo Java (JVM), và các thành phần khác để chạy các ứng dụng được viết bằng lập trình Java. JRE là một bộ của JVM.
		* Nếu bạn cần chạy các chương trình Java, nhưng không phát triển chúng, JRE là thứ bạn cần.
	* **JVM ( Java Virtual Machine- Máy ảo Java)** là một máy ảo cho phép máy tính chạy chương trình Java. 
		* JVM giúp biên dịch JAVA code thành >> byte code >> ngôn ngữ máy.
* 4 tính chất của lập trình hướng đối tượng?
	* **Tính đóng gói** = Ý nghĩa của Đóng gói, là đảm bảo rằng dữ liệu "nhạy cảm" được ẩn khỏi người dùng. Che dấu dữ liệu bên trong đối tượng
		* Cung cấp các phương thức get và set public để truy cập và cập nhật giá trị của một biến private
	* **Tính trừu tượng** = Trừu tượng hóa dữ liệu là quá trình ẩn một số chi tiết nhất định và chỉ hiển thị thông tin cần thiết cho người dùng.
		*  Nó giúp ta tập trung cái cốt lõi đối tượng. Giúp người dùng không quên bản chất đối tượng đó làm gì. (Thuộc về bản chất)
	* **Tính đa hình** = Đa hình có nghĩa là "nhiều dạng", và nó xảy ra khi chúng ta có nhiều lớp có liên quan với nhau bằng cách kế thừa.
		*  Một đối tượng thuộc các lớp khác nhau có thể hiểu cùng một thông điệp theo những cách khác nhau
	* **Tính kế thừa** = Cho phép kế thừa lại những tính năng mà một đối tượng khác đã có. Trong Java, có thể kế thừa các thuộc tính và phương thức từ lớp này sang lớp khác. Chúng tôi nhóm "khái niệm thừa kế" thành hai loại:
		* subclass (con) - lớp kế thừa từ một lớp khác
		* superclass (cha mẹ) - lớp được kế thừa từ
* Sự khác biệt của Abtracts và Interfaces class?
	* Abtracts
		* Không có constructor
		* Không hỗ trợ đa thừa kế
		* Có thể định nghĩa body của phương thức, property.
		* Có thể xác định modifier.
		* Không cần thiết phải add functionality
	* Interfaces
		* Một class có thể hiện thực nhiều interface
		* Không thể định nghĩa code xử lý, chỉ có thể khai báo
		* Mọi phương thức, property đều mặc định là public
		* Mọi phương thức, property của interface cần được hiện thực trong class.
* Overloading và Overide là gì?
	* Overloading (Nạp chồng) = là một kỹ thuật cho phép chúng ta trong cùng 1 class có thể có nhiều hơn 1 phương thức cùng trên NHƯNG  khác nhau về số lượng tham số HOẶC kiểu dữ liệu tham số.
		* Thể hiện đa hình tại compile time
		* Thêm hành vi cho phương thức
		* Có thể khác nhau về số lượng và kiểu dữ liệu của tham số
		* Xảy ra trong cùng một class
	* Overide (Ghi đè) = được sử dụng trong trường hợp lớp con kế thừa từ lớp cha và muốn định nghĩa lại một phương thức đã có ở lớp cha.
		* Thể hiện đa hình tại runtime
		* Thay đổi hành vi hiện tại của phương thức
		* Số lượng và kiểu dữ liệu của tham số phải giống nhau
		* Xảy ra ở 2 class có quan hệ kế thừa
* Kể tên 4 loại access modifier và sự khác nhau của nó? (*Phạm vi truy cập*)
	* Public = Trong lớp, trong package, ngoài package bởi lớp con, ngoài package.
	* Protected = Trong lớp, trong package, ngoài package bởi lớp con
	* Default = Trong lớp, trong package
	* Private = Trong lớp
* Constructor là gì?
	* A constructor in Java Programming is **a block of code that initializes (constructs) the state and value during object creation**. It is called every time an object with the help of a new () keyword is created. Even if you haven't specified any constructor in the code, the Java compiler calls a default constructor.
* Wrapper class là gì trong Java?
	* Wrapper class là các classes chuyển đổi các dạng data nguyên thủy sang dạng object. Tất cả các dạng data nguyên thủy đều có một Wrapper class của chính nó (*Được phân biệt bằng chữ cái đầu viết hoa hay viêt thường khi khai báo kiểu dữ liệu*).
* Làm sao để truy cập được một phương thức private?
	* Thông qua hàm getter và setter
* Làm sao để chạy một chương trình JAVA mà ko thông qua IDE?
	* Bằng lệnh java ngay trên chính terminal của máy local.
* Exception:
	* Checked  = failed tại thời điểm complie mà mình ko có try catch. Checked exception dc kế thừa từ Lớp Exception, ngoại trừ Lớp Runtime
	* Uncheckd = failed do lỗi lập trình, Exception này sẽ ko báo lỗi tại thời điểm compile. Runtime là Lớp cơ sở cho tất cả Unchecked exception.
	* Error = Failed do ngoại lệ, ko phải do lỗi lập trình hay do mình ko sử lý try catch. Kế thừa từ thằng Throwable lun.
* Data structures:
	* Array = Kích thước cố định, có thể chứa nguyên thủy và object
	* ArrayList =  Kích thước **thay đổi được**, có thể lưu trữ dữ liệu kiểu **object**, không có đồng bộ hóa.
	* Vector = cách dùng như ArrayList nhưng có đồng bộ hóa.
	* Set = ko có index và ko dc trùng lặp
	* List =  có index, có thể trùng lặp, có thể truy cập ngẫu nhiên.
	* Queue = Có index nhưng truy cập theo cấu trúc hàng đợi.
	* Stack = 
	* Map = ko có index, dữ liệu theo cặp key và value. Key cần phải độc nhất trong khi Value thì ko cần.

**Về kiến thức testing**
* Vòng đời của bug
	* New
	* Assigned
	* Open
		* Rejected
		* Duplicate
		* Not a Bug
		* Deferred
	* In progress
	* Fixed
		* Closed
		* Re-open
* Regression test là gì?
	* Regression test là một hình thức kiểm thử phần mềm để xem các chức năng cũ và mới của nó có còn hoạt động đúng sau khi thay đổi hệ thống hay không
* Smoke test là gì?
	* Smoke test là một loại Kiểm thử phần mềm được thực hiện sau khi xây dựng phần mềm để xác định rằng các chức năng quan trọng của chương trình đang hoạt động tốt.
* Sanity test là gì? 
	* Sanity testing là một loại Kiểm thử phần mềm được thực hiện sau khi nhận được một bản build phần mềm, với những thay đổi nhỏ về mã, hoặc chức năng, để xác định rằng các lỗi đã được sửa và không có vấn đề gì khác xảy ra do những thay đổi này.
* Các Test level trong Testing
	* 1. Unit Test
		* Test bởi dev
	* 2. Integration Test (API test)
		* Test bởi tester
	* 3. System Test (UI test)
		* Test bởi tester
		* Functional Test
		* Performance Test
		* Database Test
		* Security Test
		* Usability Test
		* Compatibility Test
		* Recovery Test
	* 4. Acceptance Test
		* Test bởi bên thứ 4
* Điều quan trọng trong 1 cái bug report là bug descriptions
	* Summary, priority, platform/env, description, steps, expect/actual, evident.
* Prority khác gì với Serverity?
	* Prority = Mức độ ưu tiên
		* Priority được thiết lập với tester dành cho developer được dưa trên yêu cầu của Clients.
		* Có High, Medium, Low
	* Serverity = Mức độ nghiêm trọng
		* Serverity là mức độ mà các defects có thể ảnh hưởng đến các phần mềm.
		* Có  Critical, Major, Medium, Low
* Công việc của một người automation testing là gì?
	* Develop, design, and execute script
	* Monitoring and logging defects
	* Report the result back to the test lead/client himself
* POM là gì?
	* Page Object Model
	* Theo mô hình này, đối với mỗi trang web trong ứng dụng, sẽ có lớp trang tương ứng.
	* POM là từng Web page của một web application sẽ được chuyển thành từng Class chứa các web elements và chứa các phương thức thực hiện các thao tác trên các web elements đó. 
	* Tên của các phương thức được đặt theo một thao tác cụ thể trên web elememts
* Các phần thành để có dc một test plan hoàn chỉnh:
	* 

### Câu hỏi dành cho người PV
- What is the size of the QA/QC team? 
	- Is there a dedicated QA lead for the Automation team?
- Do you guys OT regularly?
	- If you do, does it come from your own will or client requests?
- I know the firm is also an outsourcing company, so:
	- On average, how long does your guys' project take to reach the end?
	- And after the project do you guys also take on the maintenance role?
- 