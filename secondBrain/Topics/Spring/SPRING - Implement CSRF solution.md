---
Creation_date: 2025-01-31 21:08
Modification_date: Friday 31st January 2025 21:08:18
Indexes:
  - "[[spring_security]]"
  - "[[spring_thymeleaf]]"
  - "[[to_do_notes]]"
tags:
  - inProgress
---

----


When to implement CSRF solution with Spring Security and Thymeleaf:

| Cases | Does the request is GET? | Does the request is public? | Result                                  |
| ----- | ------------------------ | --------------------------- | --------------------------------------- |
| 1     | YES                      | YES                         | Not implement CSRF solution             |
| 2     | NO                       | YES                         | Apply `ignoringRequestMatchers` on CSRF |
| 3     | YES                      | NO                          | Not implement CSRF solution             |
| 4     | NO                       | NO                          | Automatically apply the CSRF solution   |



















---
## Flash cards section
