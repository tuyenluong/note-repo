---
Creation_date: 2025-01-12 23:44
Modification_date: Sunday 12th January 2025 23:44:25
Indexes:
  - "[[spring_annotation]]"
  - "[[spring_mvc]]"
---

----

Spring has provided a few specialized stereotype annotations: _@Controller_, _@Service_ and _@Repository_. They all provide the same function as _@Component_.

**They all act the same because they are all composed annotations with _@Component_ as a meta-annotation for each of them.** They are like _@Component_ aliases with specialized uses and meaning outside Spring auto-detection or dependency injection.

We could theoretically use @Component exclusively for our bean auto-detection needs if we wanted to. On the flip side, we could also [compose our specialized annotations](https://www.baeldung.com/java-custom-annotation) that use _@Component_.

However, other areas of Spring look specifically for Spring’s specialized annotations to provide additional automation benefits. **So, we should probably stick with using the established specializations most of the time.**



















---
## Flash cards section
