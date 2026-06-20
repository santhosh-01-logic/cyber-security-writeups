Turbo Intruder - My Learning Journey

Introduction

At first, Turbo Intruder looked complicated. I saw Python code, functions, objects, and many unfamiliar words. I thought Turbo Intruder was some advanced hacking tool that did magic.

After learning it step by step, I realized something important:

Turbo Intruder is not magic.

It is simply:

1. Create requests
2. Modify requests
3. Send requests
4. Receive responses
5. Analyze responses

Everything in Turbo Intruder follows this flow.

---

Mental Model

Whenever I see a Turbo Intruder script, I think:

Request
↓
Modify Request
↓
Send Request
↓
Receive Response
↓
Analyze Response

If I understand these five steps, I can understand the script.

---

The Two Most Important Functions

A Turbo Intruder script usually contains two functions.

queueRequests()

Purpose:

Create and send requests.

Example thinking:

"What requests do I want to send?"

This function is responsible for:

- Creating the engine
- Reading payloads
- Replacing markers
- Queuing requests

---

handleResponse()

Purpose:

Analyze responses.

Example thinking:

"What responses are interesting?"

This function is responsible for:

- Checking status codes
- Checking response length
- Checking response content
- Checking timing differences

---

Understanding RequestEngine

Example:

engine = RequestEngine(
    endpoint=target.endpoint,
    concurrentConnections=10
)

At first this looked scary.

Now I understand:

RequestEngine is simply the object responsible for sending requests.

The endpoint tells Turbo Intruder where to send requests.

The concurrentConnections value tells Turbo Intruder how many requests can be sent at the same time.

Think of it like workers.

1 worker:
Request
Wait
Request
Wait

10 workers:
10 requests sent simultaneously

---

Understanding Request Replacement

Example:

req = target.req.replace(
    "§username§",
    username.strip()
)

Meaning:

Take the original request.

Find:

§username§

Replace it with:

carlos

Result:

username=carlos

This is simply string replacement.

Nothing more.

---

Understanding Wordlists

Example:

for username in open("/home/ether/Documents/users.txt"):

Meaning:

Open the file.

Read one username at a time.

For every username:

Replace marker
↓
Create request
↓
Send request

---

Understanding handleResponse()

Example:

def handleResponse(req, interesting):
    table.add(req)

Meaning:

Show every response.

Useful while learning.

---

Filtering Responses

Instead of showing everything, we can filter.

Status Code

if req.status == 302:
    table.add(req)

Meaning:

Only show responses with status code 302.

---

Response Length

if req.length != 810:
    table.add(req)

Meaning:

Show responses that are different from normal.

Useful for:

- Username enumeration
- Password attacks
- Finding anomalies

---

Response Content

if b"Welcome" in req.response:
    table.add(req)

Meaning:

Show responses containing the word "Welcome".

---

The Most Important Debugging Lesson

Before learning Turbo Intruder I would ask:

"Why doesn't it work?"

Now I ask:

"What can I prove is working?"

Examples:

Is Turbo Intruder running?

raise Exception("running")

Does the file open?

raise Exception("file opened")

Are usernames being read?

raise Exception(username)

This mindset helped me more than any script.

---

Lab 1 - Username Enumeration

Goal

Find a valid username.

---

What I Did

1. Captured the login request.
2. Added a username marker.
3. Loaded usernames from a file.
4. Replaced the marker with each username.
5. Sent requests using Turbo Intruder.

Flow:

Open users.txt
↓
Read username
↓
Replace marker
↓
Send request
↓
Receive response

---

Response Analysis

I used:

table.add(req)

to view all responses.

Then I compared:

- Status codes
- Response length
- Response differences

One username behaved differently.

That username was valid.

---

Lesson Learned

Turbo Intruder did not find the username.

The server revealed the username through response differences.

Turbo Intruder simply automated the process.

---

Lab 2 - Username Enumeration via Different Responses / Timing

Goal

Find the valid username when responses behave differently.

---

What I Did

I sent the same request format repeatedly while changing usernames.

Then I observed:

- Different status codes
- Different response lengths
- Timing differences

For example:

Most usernames:

200 OK

One username:

302 Redirect

or

Different response size

or

Different timing behavior

---

How Turbo Intruder Helped

Without Turbo Intruder:

I would need to manually test many usernames.

With Turbo Intruder:

Read username
↓
Replace marker
↓
Send request
↓
Collect responses

Everything became automated.

---

Python Concepts Learned

While learning Turbo Intruder I learned:

- Variables
- Strings
- Functions
- Loops
- Conditions
- File Reading
- Objects
- Methods
- Attributes

Example:

for username in open("users.txt"):

Uses:

- for loop
- variable
- file reading

Example:

if req.status == 302:

Uses:

- condition
- comparison operator

---

Final Understanding

Before:

Turbo Intruder felt like magic.

After:

Turbo Intruder is simply:

queueRequests()
↓
Send Requests

handleResponse()
↓
Analyze Responses

Everything else is just Python.

Once I understood that, Turbo Intruder became much easier to learn.

The biggest lesson was not the tool itself.

The biggest lesson was learning to think like a debugger:

Do not ask:

"Why doesn't it work?"

Ask:

"What can I prove is working?"

That mindset applies to Python, Turbo Intruder, penetration testing, and problem solving in general.