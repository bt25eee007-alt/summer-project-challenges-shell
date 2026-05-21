# Challenge 5 : Rule Engine (YARA)

1. Install YARA on your system. Show the install steps briefly.

2. Write **3 YARA rules** that detect the following:
   - A process named `mimikatz`
   - A file path containing `/etc/shadow`
   - Any string containing `reverse_shell`

3. Create a sample text file that would trigger each rule. Run YARA against it and show the output.

4. Answer in your README:
   - What is the difference between a YARA rule matching on a file vs matching on a running process?
   - How would you add a new detection rule to a running service without restarting it?

Include your `.yar` rule files and screenshots of YARA matches.
