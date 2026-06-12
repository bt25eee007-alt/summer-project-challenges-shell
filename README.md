
























# Summer Project Selection Challenges

Submit your work as a GitHub repository. Screenshots are required wherever mentioned. Write answers directly in a `README.md` inside each challenge folder. 

**You are allowed and encouraged to use LLMs or AI Tools to help you out. What matters is that you actually ran it and understood what you did.**

Read the [Answer Format Guide](./ANS_FORMAT_README.md) before you start writing anything.

## Challenges

| # | Challenge | File |
|---|-----------|------|
| 1 | Linux Service Management | [challenge-01.md](./challenge-01.md) |
| 2 | OSQuery Setup and Exploration | [challenge-02.md](./challenge-02.md) |
| 3 | Fleet Server (gRPC) | [challenge-03.md](./challenge-03.md) |
| 4 | Kafka and Database | [challenge-04.md](./challenge-04.md) |
| 5 | Rule Engine (YARA) | [challenge-05.md](./challenge-05.md) |
| 6 | API Backend | [challenge-06.md](./challenge-06.md) |
| 7 | Frontend Dashboard | [challenge-07.md](./challenge-07.md) |



#Challenge 1: Linux Service Management Answers

### 1. Check if the service is running and find its PID
***Command used:**
'systemctl status cron'
***Output:** The service is active and running with an intial Main PID of 3015.

###2. Stop the Service
***Command used:**
'sudo systemctl stop cron'

###3. Confirm it has stopped(Verify PID is gone)
***Command used:**
'systemctl status cron'
***Output:** Service became 'inactive(dead)' and PID 3015 was given.

###4. Start the service again
***Command used:**
'sudo systemctl start cron'

###5. Kill the process directly using PID
***Command used:**
'sudo kill-9 3015'

###6. Check the service after killing it
***Command used:**
'systemctl status cron'
***Output:** Even though it kills the service, because systemd is configured to automatically restart it if it terminates abnormally, service 
status became' Active(running)' with new Main PID of 3041.


