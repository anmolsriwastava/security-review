# Paid Batch Access – Exploitation Attempt 

**Target:Phoneix Batch ACcess** 

---

## What was tested
I attempted to bypass the ₹13,999 / ₹11,999 paywall for the premium batches using client-side manipulation and payment flow interception.

## Attack Vectors Attempted

### 1. LocalStorage Injection (`persist:persist-store`)
- **What I did:** Replaced the free account's `planType: "silver"` with `planType: "gold"` in the browser's LocalStorage.
   but the backend overwrites this data on page refresh. The frontend does not serve premium content based solely on LocalStorage.

### 2. Cookie / Session Hijacking
- **What I did:** Copied the `A_TOKEN` and `A_USER` cookies from a valid paid account and injected them into a free account's browser.
   but the backend detects the ID/email mismatch and redirects the user to the purchase page.

### 3. Payment Flow Bypass
- **What I did:** Tried to intercept the Razorpay verification webhook or manually change the `order_id` in the API request.
  but the "Buy With Link" flow relies on **manual human activation**. Thus,No API grants automatic access.

---

## Conclusion
The premium batch access is currently **secure** against code-based exploits. 

The backend enforces server-side authorization correctly, and the payment flow has a human verification step that prevents automated bypass attempts.


