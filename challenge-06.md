# Challenge 6 : API Backend

Build a simple REST API using FastAPI (Python) or Express (Node.js) with these endpoints:

| Method | Endpoint | What it does |
|--------|----------|--------------|
| POST | `/nodes` | Register a node (name, os, ip) |
| GET | `/nodes` | List all nodes |
| POST | `/alerts` | Create an alert (node_id, severity, description) |
| GET | `/alerts` | Get all alerts, support `?severity=high` filter |

Use in-memory storage. No database needed.

Then add a WebSocket endpoint at `/ws/alerts`. Whenever a new alert is posted via `POST /alerts`, broadcast it to all connected WebSocket clients.

**Submit:**
- Full source code
- Screenshot of at least 3 API calls (you can use curl, Postman, or a browser)
- Screenshot showing a WebSocket client receiving a broadcast when you post a new alert

Answer in README: How does your WebSocket broadcast work when a REST endpoint is called?
