# 🔘 UI Pattern: Favorite Button — Then vs Now

This file compares how a common UI element — a "favorite button" — was implemented at Idealista (2012–2014) versus how I would build it now (2025) using modern stack.

---

### ⏳ THEN: jQuery + CSS + JSP (2013)

#### JavaScript (jQuery)

```js
$('.js-toggle-favorite').on('click', function () {
  const id = $(this).data('id');
  $.post('/api/favorites/toggle', { id });
});
```
```css
.b-fav-icon {
  background-image: url('/img/heart-empty.png');
  width: 24px;
  height: 24px;
  display: inline-block;
}
.b-fav-icon.active {
  background-image: url('/img/heart-filled.png');
}
```

⚙️ Issues (2013)
UI logic, styles and behavior were scattered

No real-time feedback or state control

AJAX success/error was manually handled

Duplication of logic in views, backend and jQuery

### 🚀 NOW: React + Tailwind + Zustand (2025)

#### Component (`FavoriteButton.tsx`)

```tsx
import { useState } from 'react';
import { toggleFavorite } from '@/lib/api';

export function FavoriteButton({ propertyId, initialState }: {
  propertyId: string;
  initialState: boolean;
}) {
  const [isFav, setIsFav] = useState(initialState);

  const handleClick = async () => {
    const updated = await toggleFavorite(propertyId);
    setIsFav(updated.is_favorite);
  };

  return (
    <button
      onClick={handleClick}
      className={`rounded-full p-2 transition-all ${
        isFav ? 'text-red-500' : 'text-gray-400'
      }`}
      aria-pressed={isFav}
    >
      {isFav ? '❤️' : '🤍'}
    </button>
  );
}
```

API Helper (lib/api.ts):
```ts
export async function toggleFavorite(id: string) {
  const res = await fetch(`/api/favorites/${id}`, { method: 'POST' });
  if (!res.ok) throw new Error('Failed to toggle');
  return res.json();
}
```

### ✅ Advantages (2025)

| **Feature**         | **THEN (2013)**                        | **NOW (2025)**                              |
|---------------------|----------------------------------------|---------------------------------------------|
| **Rendering**       | Server-side (Mustache / JSP)           | Client-side (React component)               |
| **State Management**| Manual DOM flags + jQuery handlers     | Local state via `useState`                  |
| **Styling**         | Global CSS via classes                 | Tailwind utility-first CSS                  |
| **Behavior**        | jQuery `click` → `POST`                | `async/await` with optimistic UI updates    |
| **Accessibility**   | Not enforced                           | `aria-pressed`, semantic button elements    |

🧠 Why it matters
In 2013, you had to manage everything manually: classes, events, UI state, cross-browser quirks.

In 2025, you orchestrate behavior with clarity: modular APIs, isolated state, composable UI, typed logic.

What didn’t change: the mindset behind clean separation of concerns and resilient UI behavior — that’s what I’ve carried from Idealista to now.

---

#### Template (Mustache / JSP):

```html
<div class="b-result js-toggle-favorite" data-id="{{property_id}}">
  <span class="b-fav-icon {{#is_favorite}}active{{/is_favorite}}"></span>
</div>
```

