---
Creation_date: 2025-01-28 16:02
Modification_date: Tuesday 28th January 2025 16:02:24
Indexes:
  - "[[spring_security]]"
  - "[[spring_boot]]"
  - "[[spring_boot_3.1.0]]"
  - "[[spring_security_6.1]]"
  - "[[fleeting_notes]]"
---

----


Also in this version mentioned in Index properties, `requestMatchers()` method are no longer except empty or null values as parameter. 
Or else it will produce `Pattern cannot be null or empty`  exception.

Example:
`requestMatchers("")` or `requestMatchers()`.

The correct way is `requestMatchers("/")` or  `requestMatchers("/home")`.

















---
## Flash cards section
