# 🇺🇸 CCPA / CPRA Compliance – Technical Configuration

The California Consumer Privacy Act (CCPA) and California Privacy Rights Act (CPRA) require apps and websites to:

- Inform users what personal data is collected
- Provide a way to opt out of the "sale" of their personal data
- Allow access to, and deletion of, user data upon request

---

## 🔐 Technical Implementation Plan

### 1. Add a "Do Not Sell My Personal Information" Link

```html
<a href="/do-not-sell" class="privacy-link">
  Do Not Sell My Personal Information
</a>
```
2. Use a Persistent Consent Flag
```js
window.ccpaUser = {
  id: "anonymous-123",
  doNotSell: true,
  updatedAt: new Date().toISOString()
};
Disable scripts accordingly:
```
```js
if (window.ccpaUser?.doNotSell) {
  // Prevent marketing/ad scripts from loading
}
```
3. API Endpoints (Suggested)
```http
GET    /api/privacy/user/:id         → Retrieve stored user data
DELETE /api/privacy/delete/:id       → Erase all user data (upon request)
```

4. Provide a Confirmation + Opt-out Page
Your /do-not-sell page should:

Confirm user intent to opt out

Show which cookies/data are being disabled

Link to the full privacy policy

