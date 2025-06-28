# Online Library Management System (OLMS)

An Operating Systems mini-project implementing a concurrent, socket-based Online Library Management System in C.

## Overview

This OLMS allows multiple clients to connect to a central server to perform library operations concurrently. It uses TCP sockets for communication, POSIX threads for concurrency, and file locking to ensure data consistency.

## Key Features

- **User Authentication & Role Management**
  - **Admin** can add, modify, delete, search, rent, and return books.
  - **User** can register, login, rent, return, and search books.
- **Book Management**
  - Add / modify / delete / search book records stored in a binary file.
  - Rent / return operations decrement/increment copy count.
- **Concurrency & Data Consistency**
  - Server spawns a new thread per client using `pthread_create()`.
  - Critical sections guarded by `pthread_mutex_t` and POSIX file locks.
- **Socket Programming**
  - Server listens on port 8080; clients connect via IPv4/TCP.

## Tech Stack

- **Language:** C (POSIX)
- **Concurrency:** pthreads
- **Networking:** BSD sockets (`<arpa/inet.h>`)
- **Build:** GNU Make, GCC

## Prerequisites

- Unix-like OS (Linux/macOS)
- GCC (≥ 9.x)
- make

## Folder Structure

```
.
├── Makefile
├── books.c             # Implements add/delete/modify/search/rent/return with file I/O & locks
├── server.c            # Server daemon: listens for connections, spawns threads
├── client.c            # Client app: menus for admin/user operations
├── users.c             # Implements login, registration, password change
├── books.txt           # Persistent book database (binary file)
├── users.txt           # Registered user credentials (plain text)
└── header
    ├── books.h         # Defines Book struct & book-management APIs
    └── users.h         # Defines UserType enum & auth APIs
```

## Build & Run

1. **Build everything:**
   ```sh
   make all
   ```
2. **Start the server (in one terminal):**
   ```sh
   ./server
   ```
3. **Run a client (in another terminal):**
   ```sh
   ./client
   ```
4. **Interact** using the on-screen menus for registration, login, and book operations.

## Usage Examples

- **Admin workflow:**
  1. Register or login as **admin**.
  2. Add a book: ISBN, title, author, copies.
  3. Modify / delete / search / rent / return via menu.
- **User workflow:**
  1. Login with user credentials.
  2. Rent, return, or search books.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/xyz`)
3. Commit your changes (`git commit -m "Add feature"`)
4. Push and open a Pull Request

## Author

**Aryan Singhal**
IIIT Bangalore (iMTech ’27)
Data Science Intern @ PADAAMS Innovative Technolabs Pvt Ltd
