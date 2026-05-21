# Challenge 7 : Frontend Dashboard

Build a React dashboard with two views:

**View 1 : Node List**
- Show 5 hardcoded nodes as cards (name, OS, status: online / offline / isolated)
- Clicking a card expands it to show 3–5 fake log entries for that node

**View 2 : Live Alerts**
- Connect to a WebSocket at `ws://localhost:8000/ws/alerts`
- Display incoming alerts in a table: node name, severity (color-coded), description, timestamp
- New alerts appear at the top

> Tip: You can use the API from Challenge 6 as your backend, or mock the WebSocket with a simple script.

**Submit:**
- Full source code
- Screenshot of the Node List view with one card expanded
- Screenshot of the Live Alerts view receiving a live alert

Answer in README: What happens to your WebSocket connection if the backend goes down? How would you handle reconnection?
