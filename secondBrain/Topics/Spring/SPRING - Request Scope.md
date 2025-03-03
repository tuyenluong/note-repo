---
Creation_date: 2025-01-22 00:43
Modification_date: Wednesday 22nd January 2025 00:43:16
Indexes:
  - "[[spring_mvc]]"
  - "[[to_do_notes]]"
---

----

- Spring creates a lot of instances of this bean in the app's memory for each HTTP request. So these type of beans are short lived.
- Since Spring creates a lot of instances, please make sure to avoid time consuming logic while creating the instance.
- Can be considered for the scenarios where the data needs to be reset after new request or page refresh etc...



















---
## Flash cards section
