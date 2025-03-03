---
Creation_date: 2025-03-03 09:44
Modification_date: Monday 3rd March 2025 09:44:54
Indexes:
  - "[[spring_security]]"
  - "[[to_do_notes]]"
tags:
---

----

Các cách phân quyền bằng JWT không có “một con số cố định” mà phụ thuộc vào yêu cầu và kiến trúc của hệ thống bạn. Dưới đây là một số cách phổ biến:

## Sử dụng Filter (như OncePerRequestFilter):

- Bạn có thể tạo một filter để trích xuất JWT từ header của request, sau đó xác thực và giải mã token.
- Sau đó, bạn tạo ra đối tượng Authentication và đưa vào SecurityContext.
- Cách này cho bạn sự kiểm soát chi tiết và linh hoạt.

## Sử dụng Spring Security Resource Server với JwtDecoder:

- Khi dùng Resource Server, Spring Security đã tích hợp sẵn các cơ chế xử lý JWT.
- Bạn cấu hình JwtDecoder để xác thực token, từ đó tự động mapping các claims thành authorities.
- Phương pháp này giúp giảm bớt code tùy chỉnh và tận dụng được các tính năng tích hợp sẵn của Spring Security.

## Kết hợp với UserDetailsService:

- Trong một số trường hợp, JWT token có thể chỉ chứa thông tin cơ bản (như user id, username) mà không đủ để xác định đầy đủ quyền hạn.
- Khi đó, bạn có thể sử dụng UserDetailsService để load thêm thông tin người dùng từ cơ sở dữ liệu và cập nhật lại authorities cho Authentication.
- Phương pháp này hữu ích khi bạn cần kết hợp giữa thông tin trong token và dữ liệu thực tế từ hệ thống.

## Lựa chọn thường dùng nhất:

Hiện nay, với sự phát triển của Spring Security, việc sử dụng Resource Server với JwtDecoder đang được ưa chuộng vì nó cho phép xử lý JWT một cách tự động, giảm bớt code tự viết và dễ dàng tích hợp. Tuy nhiên, nếu ứng dụng của bạn có những yêu cầu đặc biệt (ví dụ cần load thêm thông tin người dùng từ DB), việc kết hợp với UserDetailsService sẽ là lựa chọn phù hợp.

Tóm lại, lựa chọn phương pháp nào phụ thuộc vào cách bạn thiết kế hệ thống, mức độ tin cậy của JWT token và yêu cầu về việc quản lý chi tiết thông tin người dùng.



















---
## Flash cards section
