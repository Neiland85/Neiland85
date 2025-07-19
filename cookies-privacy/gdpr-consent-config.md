# 🇪🇺 GDPR Compliance – Cookie & Tracking Strategy

## Key Principles

- No tracking without prior consent
- Explicit opt-in for each category: essential, functional, analytics, marketing
- Consent log stored with timestamp, device info, language
- Consent can be withdrawn at any time
- Separate cookie categories with dynamic toggles

## Technical Implementation

- Consent modal on first visit (before setting non-essential cookies)
- Cookies only stored if `window.gdprConsent = { analytics: true }`
- Google Analytics, Facebook Pixel and other scripts only triggered after consent

## Example toggle logic

```js
if (window.gdprConsent?.analytics) {
  loadGoogleAnalytics();
}
```
Store gdprConsent as a signed JSON in localStorage, with timestamp and language

## ✅ `ccpa-config.md`

```md
# 🇺🇸 CCPA / CPRA Compliance – Data Control

## User Rights

- Right to know what data is collected
- Right to delete personal data
- Right to opt-out of the sale of personal data

## Site Obligations

- Show "Do Not Sell My Info" link
- Give access to stored data if requested
- Accept data deletion requests

## Technical Suggestions

- `ccpaUser = { id: "anon123", doNotSell: true }` stored in localStorage
- Analytics / Ad scripts disabled if `doNotSell === true`
- API endpoint: `DELETE /api/privacy/delete/:userId`
```

## Suggested UI link

```html
<a href="/do-not-sell" class="privacy-link">Do Not Sell My Personal Information</a>
```

---

## ✅ `consent-banner.js`

```js
// 🍪 Simple GDPR + CCPA Consent Banner
(function () {
  const banner = document.createElement('div');
  banner.id = 'consent-banner';
  banner.innerHTML = `
    <div style="position:fixed;bottom:0;width:100%;background:#000;color:#fff;padding:1em;text-align:center;z-index:9999">
      We use cookies to improve your experience. 
      <button id="accept-cookies">Accept</button>
      <a href="/privacy">Learn more</a>
    </div>
  `;
  document.body.appendChild(banner);

  document.getElementById('accept-cookies').onclick = function () {
    localStorage.setItem('gdprConsent', JSON.stringify({ analytics: true, marketing: false }));
    banner.remove();
    location.reload();
  };
})();
```
