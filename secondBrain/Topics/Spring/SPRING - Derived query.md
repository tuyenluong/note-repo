---
Creation_date: 2025-03-06 00:40
Modification_date: Thursday 6th March 2025 00:40:24
Indexes:
  - "[[spring_boot]]"
  - "[[to_do_notes]]"
---

----

Spring Data JPA is a powerful tool that provides an extra layer of abstraction on top of existing JPA providers like Hibernate. The derived query feature is one of the most loved features of Spring Data JPA.

## Supported Keywords in Derived Query Methods

| Keyword      | Sample Method Name               | Sample Query that Forms by JPA |
|-------------|---------------------------------|--------------------------------|
| Distinct    | findDistinctByLastnameAndFirstname | `SELECT DISTINCT ... WHERE x.lastname = ?1 AND x.firstname = ?2` |
| And         | findByLastnameAndFirstname     | `... WHERE x.lastname = ?1 AND x.firstname = ?2` |
| Or          | findByLastnameOrFirstname     | `... WHERE x.lastname = ?1 OR x.firstname = ?2` |
| Is, Equals  | findByFirstname, findByFirstnameIs, findByFirstnameEquals | `... WHERE x.firstname = ?1` |
| Between     | findByStartDateBetween         | `... WHERE x.startDate BETWEEN ?1 AND ?2` |
| LessThan    | findByAgeLessThan              | `... WHERE x.age < ?1` |
| LessThanEqual | findByAgeLessThanEqual       | `... WHERE x.age <= ?1` |
| GreaterThan | findByAgeGreaterThan          | `... WHERE x.age > ?1` |
| GreaterThanEqual | findByAgeGreaterThanEqual | `... WHERE x.age >= ?1` |
| After       | findByStartDateAfter          | `... WHERE x.startDate > ?1` |
| Before      | findByStartDateBefore         | `... WHERE x.startDate < ?1` |
| IsNull, Null | findByAge(Is)Null            | `... WHERE x.age IS NULL` |
| IsNotNull, NotNull | findByAge(Is)NotNull   | `... WHERE x.age IS NOT NULL` |
| Like        | findByFirstnameLike           | `... WHERE x.firstname LIKE ?1` |
| NotLike     | findByFirstnameNotLike        | `... WHERE x.firstname NOT LIKE ?1` |
| StartingWith | findByFirstnameStartingWith  | `... WHERE x.firstname LIKE ?1 (appended %)` |
| EndingWith  | findByFirstnameEndingWith    | `... WHERE x.firstname LIKE ?1 (prepended %)` |
| Containing  | findByFirstnameContaining    | `... WHERE x.firstname LIKE ?1 (wrapped in %)` |
| OrderBy     | findByAgeOrderByLastnameDesc  | `... WHERE x.age = ?1 ORDER BY x.lastname DESC` |
| Not         | findByLastnameNot            | `... WHERE x.lastname <> ?1` |
| In          | findByAgeIn(Collection<Age> ages) | `... WHERE x.age IN ?1` |
| NotIn       | findByAgeNotIn(Collection<Age> ages) | `... WHERE x.age NOT IN ?1` |
| True        | findByActiveTrue()           | `... WHERE x.active = TRUE` |
| False       | findByActiveFalse()          | `... WHERE x.active = FALSE` |
| IgnoreCase  | findByFirstnameIgnoreCase    | `... WHERE UPPER(x.firstname) = UPPER(?1)` |
![[Derived query1.png]]

![[Derived query2.png]]

![[Derived query3.png]]















---
## Flash cards section
