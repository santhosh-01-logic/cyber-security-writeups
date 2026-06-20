Username Enumeration via Response Timing Lab Write-up

Overview

This lab focused on username enumeration through response timing differences. Initially, I struggled because I confused this lab with the previous subtly different response lab. Instead of carefully reading the lab requirements, I assumed the solution would involve analyzing response messages rather than response times.

This taught me an important lesson: always read the lab description and flags carefully before starting. Even a small difference in wording can completely change the attack methodology.

---

Initial Mistake

Previously, I had learned about username enumeration using subtly different responses. Because of that, I automatically assumed this lab was similar.

However, this lab was specifically about response timing.

Instead of looking for different error messages, I should have been measuring how long the server took to respond. Since I didn't properly read the lab instructions at first, I wasted time looking at response content rather than response timing.

After realizing my mistake, I became more cautious and started focusing on timing-based analysis.

---

Attempting the Attack

I used Burp Suite Intruder and tested multiple usernames while observing the response times.

I noticed that some requests took slightly longer than others, indicating that the application was processing valid usernames differently from invalid ones.

To automate the process, I experimented with different Intruder attack types, including:

- Cluster Bomb
- Multiple payload configurations
- Repeated timing tests

However, I kept encountering problems.

---

The Real Challenge: IP-Based Rate Limiting

The application had IP-based brute force protection enabled.

Because I was sending many requests from the same IP address, the application began blocking or rate-limiting my requests. This made the timing results unreliable and prevented successful enumeration.

At this point, I checked the solution and learned about the use of the X-Forwarded-For header.

---

Bypassing the Protection

The solution involved modifying the request by adding a custom header:

X-Forwarded-For: 127.0.0.X

In Burp Intruder:

1. Add a new header below the Content-Type header:
   
   X-Forwarded-For: 127.0.0.§X§

2. Mark two payload positions:
   
   - Username field
   - Last octet of the X-Forwarded-For header

3. Use a Pitchfork Attack.

Why Pitchfork?

Pitchfork allows multiple payload sets to advance simultaneously.

For example:

Username| X-Forwarded-For
user1| 127.0.0.1
user2| 127.0.0.2
user3| 127.0.0.3

Each request appears to come from a different IP address.

---

Why This Works

The web application tracks login attempts based on IP addresses.

By changing the value of the X-Forwarded-For header on every request, the application believes each request is coming from a different client.

As a result:

- Rate limiting is bypassed.
- Brute force protection becomes ineffective.
- Accurate timing measurements can be collected.
- Valid usernames can be identified successfully.

---

Result

After switching to the Pitchfork attack and rotating the X-Forwarded-For header values, the timing differences became usable again.

Using the response timing information, I successfully identified the valid username and eventually obtained the correct credentials to solve the lab.

---

Key Lessons Learned

- Always read the lab description carefully before starting.
- Do not confuse response-based enumeration with timing-based enumeration.
- Response timing can reveal valid usernames even when error messages are identical.
- Web applications often implement IP-based rate limiting.
- The X-Forwarded-For header can sometimes be abused to bypass weak IP-based protections.
- Burp Suite's Pitchfork attack is useful when multiple payload positions must change together.
- Understanding why an attack fails is just as valuable as successfully completing it.