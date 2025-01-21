---
Creation_date: 2025-01-22 01:11
Modification_date: Wednesday 22nd January 2025 01:11:11
Indexes:
  - "[[spring_core_&_mvc]]"
---

----


| **Scope**       | **Description**                                                                                         | **Use Case**                                                                                          | **Pros**                                                                                                          | **Cons**                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **singleton**   | A single instance of the bean is created and shared across the entire application context.              | **Default scope**. Suitable for stateless beans like service classes, utility components, and DAOs.   | - Memory efficient (single instance).<br>- Simplifies resource sharing.<br>- Thread-safe if properly implemented. | - Can introduce issues if not thread-safe.<br>- Shared state may lead to unintended side effects. |
| **prototype**   | A new instance of the bean is created every time it is requested.                                       | Suitable for **stateful beans** or beans requiring unique state for each use (e.g., a shopping cart). | - Provides fresh instances.<br>- No shared state, eliminating unintended interference.                            | - Resource-intensive.<br>- Developer must manage lifecycle explicitly.                            |
| **request**     | A new bean instance is created for each HTTP request. Scoped to the lifecycle of a single HTTP request. | Suitable for web apps where beans should be tied to the lifecycle of a single HTTP request.           | - Ideal for request-specific data.<br>- Simplifies managing request-scoped state.                                 | - Limited to web applications.<br>- Becomes invalid after the HTTP request is complete.           |
| **session**     | A single instance of the bean is created and shared per HTTP session.                                   | Suitable for **user session data**, like authentication tokens or user preferences.                   | - Persistent for session lifecycle.<br>- Simplifies session-level data management.                                | - Limited to web applications.<br>- Potential for excessive memory usage in large apps.           |
| **application** | A single instance of the bean is shared across the entire ServletContext.                               | Suitable for **application-wide components**, such as caching or application settings.                | - Shared across the application.<br>- Ideal for global, immutable data.                                           | - Not request/session-aware.<br>- May lead to memory bloat for rarely-used components.            |
| **websocket**   | A single instance of the bean is created per WebSocket session.                                         | Suitable for **real-time communication**, tracking data for individual WebSocket sessions.            | - Isolated state for each WebSocket session.<br>- Simplifies session-level WebSocket data.                        | - Limited to WebSocket-based apps.<br>- Can increase memory usage for many concurrent sessions.   |

### General Recommendations:
- **Use singleton**: For most service, repository, and utility classes. It’s efficient and works for stateless components.
- **Use prototype**: When you need a new stateful instance every time the bean is requested.
- **Use request/session/application**: For web applications when the lifecycle of the bean should match that of the request, session, or application context.
- **Use websocket**: In WebSocket applications to manage per-session communication data.

















---
## Flash cards section
