
# **COSC1295 Advanced Programming - Technology Reflection Report**

**Student Name:** Danial Awais Ansari  
**Student ID:** S4119075  
**Assignment:** Healthcare Management System  
**Date:** October 25, 2025

---

## **Technologies Used and Key Design Decisions**

This healthcare management system demonstrates advanced Java programming using **Java 11**, **JavaFX 17** for the graphical interface, **SQLite** for database archiving, and **JUnit 5** for testing. The architecture employs the **Singleton design pattern** for `CareHome`, `DatabaseManager`, and `AuditLogger` classes to ensure single sources of truth and prevent resource conflicts. The object-oriented design features a three-level inheritance hierarchy (`Person` → `Staff`/`Patient` → `Doctor`/`Nurse`/`Manager`) demonstrating encapsulation, polymorphism through role-based permissions, and clear separation of concerns following the Model-View-Controller pattern.

***

## **JavaFX: Strengths, Limitations, and Alternatives**

**Strengths:** JavaFX's FXML architecture cleanly separates UI layout from business logic, enabling visual design through Scene Builder. The framework provides rich controls for creating the ward bed layout with color-coded gender indicators and real-time system clock updates. Cross-platform compatibility ensures consistent behavior across Windows, Mac, and Linux operating systems.

**Limitations:** The Java Platform Module System required explicit module configuration (`--add-modules javafx.controls,javafx.fxml`), complicating initial setup. UI threading restrictions meant background operations needed careful coordination with the JavaFX Application Thread. The framework has a steeper learning curve than alternatives like Swing, and online community support is smaller compared to web technologies.

**Alternative:** For multi-location deployment, a **Spring Boot backend with React frontend** would enable browser-based access without client installation, supporting concurrent users across facilities. This would increase architectural complexity but provide better scalability and modern user experience.

***

## **SQLite Database: Implementation and Trade-offs**

**Strengths:** SQLite's embedded architecture eliminates server configuration—the entire database exists in a single file, perfectly satisfying the assignment's requirement for auditor-accessible archived data. Full SQL support includes foreign keys, transactions, and complex queries. Zero-configuration deployment and portability make it ideal for desktop applications.

**Limitations:** SQLite restricts concurrent writes to a single process, limiting multi-user scenarios. Network access requires file sharing rather than client-server connections. Foreign key enforcement must be explicitly enabled via `PRAGMA foreign_keys = ON`, as it's disabled by default for backward compatibility.

**Alternative:** For multi-facility systems, **PostgreSQL** would provide concurrent write access, role-based authentication, and stored procedures. Migration would be straightforward due to similar SQL syntax, with connection pooling (HikariCP) managing concurrent access efficiently.

***

## **Java Serialization: Persistence Strategy**

**Strengths:** Built-in object serialization requires no external libraries and automatically handles object graphs including complex relationships. The `transient` keyword elegantly excludes non-serializable resources like database connections from persistence.

**Limitations:** Binary format prevents human inspection or editing of save files. Versioning challenges arise when modifying class structures without careful `serialVersionUID` management. Security vulnerabilities exist when deserializing untrusted data.

**Alternative:** **JSON serialization** using Jackson or Gson libraries would provide human-readable, language-agnostic, and version-tolerant persistence at the cost of explicit configuration requirements.

***

## **Key Challenges and Solutions**

**Challenge 1 - Roster Validation:** Implementing time-based shift checking required understanding Java 8's modern date/time API. The `LocalDateTime` and `DayOfWeek` classes proved superior to legacy date handling for validating whether staff members are currently on shift.

**Challenge 2 - Gender Segregation:** Ensuring patients of different genders don't share rooms required checking existing occupants before assignment while allowing empty rooms to accept any gender initially. This maintains flexibility without requiring fixed room-level gender properties.

**Challenge 3 - Real-Time UI Updates:** Initial attempts to update the system clock using thread sleep operations blocked the entire interface. The solution employed JavaFX's `Timeline` API for non-blocking scheduled updates on the UI thread.

---

## **Testing Strategy and Lessons Learned**

Comprehensive JUnit testing covered business logic validation (authorization, bed occupancy, patient movement), polymorphic behavior verification, and input validation. Tests included both positive scenarios (valid operations succeed) and negative scenarios (exceptions thrown appropriately). The most valuable lesson was discovering bugs early through testing: developing tests alongside production code rather than afterward makes debugging significantly easier and builds confidence in refactoring decisions.

***

## **Personal Reflection and Future Enhancements**

**Key Learnings:** This project deepened understanding of when to apply design patterns (Singleton for shared state), trade-offs between technology choices (embedded vs. client-server databases), and the importance of maintainable code structure over clever implementations. Writing comprehensive tests proved essential for ensuring business rule compliance.

**What I'd Do Differently:** Start with test-driven development rather than adding tests afterward. Create class diagrams before coding to visualize relationships. Use version control with more granular commits documenting design rationale. Refactor incrementally to avoid accumulating technical debt.

**Future Enhancements:** (1) Web-based interface for multi-location access. (2) Analytics dashboard with charts showing bed occupancy trends and staff workload. (3) Notification system for medication reminders and shift alerts. (4) Database migration tools (Flyway/Liquibase) for schema versioning. (5) Enhanced role-based access control with configurable permissions.

***

## **Conclusion**

This assignment demonstrated that effective software engineering balances technical excellence with practical delivery. The Singleton pattern ensured data consistency, SQLite provided compliant portable archiving, and JavaFX delivered functional visualization. Most importantly, the project reinforced that code maintainability—through clear structure, consistent naming, and comprehensive exception handling—matters more than technical complexity. The system successfully meets all assignment requirements and provides a solid foundation for future enhancement to support multi-user web-based deployment.
