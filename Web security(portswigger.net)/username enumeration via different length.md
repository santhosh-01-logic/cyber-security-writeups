Username Enumeration and Password Brute Force Lab Write-up

Objective

Find a valid username through username enumeration and then brute-force the password using Burp Suite Intruder.

---

Step 1: Open Burp Suite

1. Start Burp Suite.
2. Open Burp's built-in browser (or configure Firefox to use Burp as a proxy).
3. Access the lab URL.
4. Navigate to the login page.

---

Step 2: Capture the Login Request

1. Enter any username and password.
2. Submit the login form.
3. Go to Proxy → HTTP History.
4. Locate the login request.
5. Right-click the request and select Send to Intruder.

---

Step 3: Username Enumeration

Configure Intruder

1. Open Intruder.
2. Go to the Positions tab.
3. Clear all automatically generated payload markers if necessary.

Important Mistake I Made

The payload markers must surround the entire value.

Correct:

username=§candidate§

Wrong:

username=candidate§

or

username=§candidate

If the payload markers are not placed correctly at both the beginning and end of the value, Intruder will not replace the payload and the attack will fail.

I made this mistake several times and couldn't understand why the attack wasn't working. After checking explanations and troubleshooting, I realized the payload markers were incorrect.

Add Username Payload

1. Highlight the username value.
2. Click Add §.
3. Leave the password field fixed.
4. Select Sniper attack type.
5. Go to Payloads.
6. Paste the provided username list.
7. Start the attack.

Identify the Valid Username

1. Review the responses.
2. Look for differences in:
   - Response length
   - Status code
   - Redirect behavior
3. One response should stand out from the others.
4. The username associated with that response is the valid username.

---

Step 4: Password Brute Force

1. Return to the original login request.
2. Replace the username with the valid username discovered earlier.
3. Highlight the password value.
4. Add payload markers around the password field.
5. Keep the username fixed.
6. Select Sniper attack type.
7. Load the password wordlist.
8. Start the attack.

---

Step 5: Identify the Correct Password

Look for a response that differs from the others.

Common indicators:

- Different response length
- Different status code
- Redirect to another page
- Successful login response

The password associated with that response is the correct password.

---

Step 6: Log In

1. Return to the login page.
2. Enter the valid username.
3. Enter the discovered password.
4. Submit the form.

The lab should now be solved successfully.

---

Key Lesson

Always verify that the Intruder payload markers (§) are placed correctly around the entire field value.

Incorrect payload placement was the main reason my attack failed multiple times.
