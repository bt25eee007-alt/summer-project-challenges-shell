# Challenge 4 : Kafka and Database

> **Requirement:** Docker and Docker Compose installed.

1. Set up Apache Kafka using Docker Compose (single broker setup is fine). Take a screenshot of the containers running.

2. Create a topic called `endpoint-logs`.

3. Using the Kafka CLI tools (inside the container is fine):
   - Produce at least 5 messages to the topic manually
   - Consume and print all messages from the topic
   - Take a screenshot of both

4. Write a short Python script (or any language) that:
   - Produces 10 fake log events to `endpoint-logs`
   - Each event must have: `node_id`, `timestamp`, `event_type`, `details`
   - Consumes them back and prints each one

Include the script in your repo and a screenshot of the output.
