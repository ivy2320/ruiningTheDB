B
🔹 1. Union-Based SQLi

Uses the UNION operator to combine results of two queries.

Attacker can extract data directly into the webpage.

Example:

' UNION SELECT username, password FROM users --

🔹 2. Error-Based SQLi

Relies on database error messages to reveal information.

Example:

' AND 1=CONVERT(int, (SELECT @@version)) --


The error output may leak database details.

🔹 3. Boolean-Based Blind SQLi

No errors or direct output shown.

Attacker asks true/false questions via payloads.

Example:

' AND SUBSTRING(DATABASE(),1,1)='t' --


If page looks different, guess is correct.

🔹 4. Time-Based Blind SQLi

No visible difference in page output.

Attacker measures response time to extract data.

Example:

' OR IF(1=1, SLEEP(5), 0) --


Delay = condition true, fast response = false.

🔹 Prevention

Use prepared statements (parameterized queries).

Apply least privilege for DB users.

Validate and sanitize input.

Use WAF as extra defense.

✅ Takeaway: Even without direct errors, attackers can exploit SQLi using logic or timing. Always code securely.
