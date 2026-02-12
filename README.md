# The Silent Server - Auth Debugging Fixes

Hey! I’ve completed the assignment. This project was a broken Express.js backend where the authentication flow was failing at every step. I’ve debugged the code, fixed the logic, and verified it using PowerShell.

## 🛠 How I Fixed the Bugs

### 1. Login Logic
The server was generating the OTP but not showing it clearly. I ensured the console correctly logs the **OTP** and the **Session ID** so we can actually use them for the next steps.

### 2. OTP Verification (Data Types)
The verification was failing because of a data type mismatch (comparing a String to a Number). I used `Number()` to ensure the check is accurate. I also enabled `cookie-parser` so the server can actually "remember" the user by setting a session cookie.

### 3. Token Generation (Cookie vs. Header)
The `/auth/token` route was looking for the session ID in the wrong place (headers) or using hardcoded strings. I updated it to read the `session_token` directly from the **cookies** provided by the verification step.

### 4. Protected Route & Middleware
The middleware was crashing because it didn't check if the Authorization header existed before trying to read it. I added a safety check and used `.split(' ')` to properly strip the "Bearer " prefix so the JWT can be verified.

---

## 🚀 How to Run & Verify

1. **Install:** `npm install`
2. **Start:** `npm start`
3. **Test:** Run the commands in `output.txt` to see the flow in action.

## ✅ Success Flag
Once the flow is complete, the `/protected` route returns a unique flag based on my email. 
**My Flag:** `FLAG-c2luZ2gubHVja3kudGVjaDExQGdtYWlsLmNvbV9DT01QTEVURURfQVNTSUdOTUVO...`
