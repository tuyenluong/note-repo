---
Creation_date: 2025-03-07 13:25
Modification_date: Friday 7th March 2025 13:25:30
Indexes:
  - "[[spring_boot]]"
  - "[[to_do_notes]]"
---

----

`GenerationType.AUTO` is always  trying to generate new IDs **without checking the existing ones in the database**. This often results in conflicts when inserting new records.
## Why is this happening?

- The `AUTO` strategy lets **Hibernate decide** how to generate the ID, which can vary depending on the database.
- If your database doesn’t properly track the last inserted `CONTACT_ID`, it might **start at 0** instead of continuing from the existing IDs.
- If the ID column isn't set to `AUTO_INCREMENT` in the database, Hibernate won't know where to continue.

## How to Fix It

### Use `IDENTITY` Instead of `AUTO`

Try switching to `GenerationType.IDENTITY`, which tells Hibernate to use the **database's auto-increment mechanism**:
```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
@Column(name = "contact_id")
private int contactId;
```

**Why this works:**  
This ensures that the database itself controls the ID generation, avoiding conflicts.















---
## Flash cards section
