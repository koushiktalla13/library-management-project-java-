# Library Management System (Java)

A console-based application to manage books, members, issuing, returning, fines and overdue tracking.

## How to run
```
javac *.java
java Main
```
Requires JDK 8 or higher. Data is saved automatically to `library.dat` when you exit with option 0.

## Features
- Add books, register members (Student / Faculty)
- View and search books (by title or author)
- Issue and return books with automatic due dates and fine calculation
- View a member's borrowed books, overdue books and full transaction history
- Data persists between runs (file I/O)

## Rules
| Member  | Max books | Loan period | Fine per late day |
|---------|-----------|-------------|-------------------|
| Student | 3         | 14 days     | Rs. 2             |
| Faculty | 5         | 30 days     | Rs. 1             |

## Java concepts demonstrated
| Concept | Where |
|---|---|
| Classes and objects | Book, Member, Transaction, Library |
| Encapsulation | private fields with getters/setters; `getBorrowedBookIds()` returns an unmodifiable list |
| Inheritance | Student and Faculty extend Member; custom exceptions extend LibraryException |
| Abstraction | abstract class Member with abstract methods |
| Polymorphism | `member.getMaxBooks()` / `getLoanDays()` / `getFinePerDay()` behave differently per subclass |
| Collections | ArrayList, LinkedHashMap, List/Map interfaces, generics |
| Exception handling | custom checked exceptions, try/catch, try-with-resources, multi-catch |
| File I/O | serialization with ObjectOutputStream / ObjectInputStream (FileHandler) |
| Date/Time API | LocalDate, ChronoUnit.DAYS.between for fine calculation |
| Control flow | switch menu, while loops, input validation |
| Separation of concerns | Main = user interface, Library = logic, FileHandler = storage |

## Demo tip (to show fines)
When issuing a book, enter a past issue date (e.g. 2026-09-01). Returning it today will show a late fine, and option 8 lists it as overdue while it is still out.
