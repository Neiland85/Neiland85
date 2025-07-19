# 🏛️ Case Study: Idealista UI & Backend Evolution (2012–2014)

> Role: Backend Developer with UI responsibilities  
> Company: Idealista (Madrid, Spain)  
> Period: Oct 2012 – Jul 2014  
> Key Tech: Java · JSP · jQuery · Mustache.js · HTML5 · CSS3 · RESTful APIs · Token Auth · JSON  
> Transition Era: From monolith to modular thinking

---

## 🔍 Context & Challenges

I joined Idealista during a pivotal technical transformation:  
We were evolving from a monolithic backend into a modular architecture with early RESTful APIs.  
At the same time, frontend interfaces were being built **without frameworks** — just raw HTML, jQuery, and server-side templates (JSP or Mustache).

Our interfaces powered complex features like:

- 🔎 Real estate search filters
- 🧮 Dynamic scoring of results
- 📊 Management of large-scale real estate data
- 🔐 Token-based API auth and JSON-first logic

The focus was always: **efficiency, clarity, reliability**.

---

## 🧱 Sample UI+Logic Pattern (2013 Style)

Even though I was on backend, we had to understand and sometimes contribute to frontend architecture. Here’s how we structured interactive components:

```html
<!-- Mustache or JSP -->
<div class="b-result js-toggle-favorite" data-id="{{property_id}}">
  {{title}}
  <span class="b-fav-icon {{#is_favorite}}active{{/is_favorite}}"></span>
</div>
js
```
<!-- jQuery logic -->
$('.js-toggle-favorite').on('click', function () {
  const id = $(this).data('id');
  $.post('/api/favorites/toggle', { id });
});

<!-- css -->
.b-fav-icon {
  background: url('/img/heart-empty.png');
}
.b-fav-icon.active {
  background: url('/img/heart-filled.png');
}

🧠 Lessons Learned
Component logic was split across backend + frontend + CSS

No React. No Webpack. No real state management.

We had to name components clearly, reuse blocks manually, and debug across server and browser

Changes required deep understanding of the backend-rendered HTML pipeline

🛠️ What I Actually Did
As a backend developer, I contributed to:

🧮 Scoring algorithms for property relevance

📦 Dynamic filtering modules for massive search datasets

⚙️ First generation of RESTful endpoints with JSON & token auth

🔄 Refactoring legacy JSP views toward partial, reusable logic

But I also learned to:

Think like an architect, even before being called one.

Idealista taught me that designing a solution was more than writing code — it was about understanding scope, dependencies, execution, and cost of change.

### 🔁 Then vs Now (2025)

| **Aspect**         | **2013**                                              | **2025**                                                 |
|--------------------|-------------------------------------------------------|----------------------------------------------------------|
| **UI Components**  | jQuery + HTML + CSS manually composed                 | React + Tailwind + headless CMS or design system         |
| **State Management** | DOM data attributes + jQuery state                  | `useState`, `useReducer`, global stores                  |
| **APIs**           | Token-based REST via JSP endpoints                    | OpenAPI + JWT + event-driven contracts                   |
| **CSS**            | Manual naming (BEM-inspired)                          | Tailwind, CSS Modules, PostCSS                           |
| **Tooling**        | Bash scripts, Ant, sometimes Makefiles                | TurboRepo, Nx, Vite, GitHub Actions                      |
| **Deployment**     | Internal tools + manual validation via VPN            | CI/CD pipelines + Preview Environments + Canary releases |

📌 Why this matters
Even though the tech was primitive by today’s standards, the thinking was already architectural.

I learned modularity before modules

I practiced separation of concerns without a build system

I developed code for users at massive scale with real-world constraints

This experience grounded my evolution into modern backend & system architecture.

// jQuery logic
$('.js-toggle-favorite').on('click', function () {
  const id = $(this).data('id');
  $.post('/api/favorites/toggle', { id });
});

.b-fav-icon {
  background: url('/img/heart-empty.png');
}
.b-fav-icon.active {
  background: url('/img/heart-filled.png');
}

```html
<!-- Mustache or JSP -->
<div class="b-result js-toggle-favorite" data-id="{{property_id}}">
  {{title}}
  <span class="b-fav-icon {{#is_favorite}}active{{/is_favorite}}"></span>
</div>
```
