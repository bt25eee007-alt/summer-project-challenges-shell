# Challenge 3 : Fleet Server (gRPC)

> **Language:** C, C++, Rust, or Go. Python is not allowed.

Build a minimal gRPC server that does the following:

1. **Enroll a node** : accepts a node name and OS type, assigns it a unique ID, stores it in memory
2. **List all nodes** : returns the list of all enrolled nodes with their IDs

Write a client (same language or any language) that:
- Enrolls 3 different nodes
- Calls the list endpoint and prints all enrolled nodes

**Submit:**
- Full source code + your `.proto` file
- Screenshot of the server running
- Screenshot of the client output showing all 3 enrolled nodes
