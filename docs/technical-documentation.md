# Technical Documentation

---

## 1. Project Overview

This project is a static personal portfolio website built using:

* HTML5
* CSS3
* JavaScript 

It does not use any frameworks or backend services. The goal is to demonstrate advanced front-end development skills including interactivity, state management, API integration, and performance optimization.

The website is fully responsive and supports both light and dark themes.

---

## 2. Technologies Used

### HTML

Provides the structure of the website and organizes content into clear sections such as navigation, hero, projects, and contact.

### CSS

Handles layout, styling, animations, and responsive design. Includes:

* Flexbox layouts
* Responsive media queries
* Transitions and animations
* Dark mode styling

### JavaScript

Implements all interactive features including logic handling, state management, and API integration.

### External API

* Wikipedia REST API for dynamic programming facts

---

## 3. Website Structure

| Section    | Description                     |
| ---------- | ------------------------------- |
| Navigation | Links + theme toggle            |
| Hero       | Introduction + greeting + timer |
| Tech Facts | API integration                 |
| About      | Personal info                   |
| Journey    | Timeline of academic milestones |
| Projects   | Interactive project system      |
| Contact    | Form validation                 |

---

## 4. User Interaction Flow (Step-by-Step Guide)

### 1. Landing Experience

* User sees hero section
* Dynamic greeting appears based on time
* Visit timer starts automatically

---

### 2. Navigation

* User clicks navbar links
* Smooth scroll to sections

---

### 3. Journey Section

* Timeline items are hidden by default
* As the user scrolls, each item animates into view when it reaches 85% of the viewport height
* Items hide again when scrolling back up

---

### 4. Projects Section (Main Interaction Area)

#### Search (Real-time Filtering)

* User types in search bar
* Projects update instantly
* Case-insensitive matching
* If no results → message appears

---

#### Sorting

* User selects:

  * Default
  * A → Z
  * Z → A
* Projects reorder dynamically

---

#### Accordion (Expand/Collapse)

* Clicking a project:

  * Opens description
  * Closes other projects
* Uses smooth animation

---

### 5. API Feature (Tech Facts)

* User clicks "Generate Fact"
* Loading spinner appears
* Fact is fetched from API
* Duplicate facts are avoided using a Set
* Retries automatically if duplicate
* Error message shown if request fails

---

### 6. Contact Form

* User fills form

Validation includes:

* Required fields check
* `.trim()` prevents empty spaces
* Email validation using regex
* Error or success message displayed
* Form resets after success

---

### 7. Theme Toggle (State Management)

* User switches between light/dark mode
* Preference stored in `localStorage`
* Theme persists after refresh

---

### 8. Additional Dynamic Features

* **Visit Timer** updates every second
* **Dynamic Greeting** based on time of day
* **Scroll Reveal Animations** when elements enter viewport

---

## 5. JavaScript Features Implementation

### Initialization

```javascript
document.addEventListener("DOMContentLoaded")
```

---

### Implemented Features

#### 1. Dark Mode

* Uses `localStorage`
* Toggles `dark` class

#### 2. Dynamic Greeting

* Uses `Date().getHours()`
* Displays good morning/good afternoon/good evening

#### 3. Visit Timer

* Uses `setInterval`
* Displays seconds and minutes

#### 4. Search

* Listens to `input` event on the search field
* Matches the **first word** of each project title using `.startsWith()`
* Shows or hides cards by setting `display: flex` or `display: none`
* Displays an empty message if no cards are visible

#### 5. Sorting

* Converts `NodeList` to array, sorts using `.localeCompare()`
* Reorders cards in the DOM using `appendChild`
* Restores original order using `data-index` attribute set at initialization

#### 6. Accordion

* Uses `max-height` animation
* Only one open at a time

#### 7. Form Validation

* `.trim()` for empty inputs
* Regex for email
* Dynamic feedback messages

#### 8. API Integration

* Fetches from `https://en.wikipedia.org/api/rest_v1/page/summary/{language}`
* Uses retry logic (max attempts)
* Prevents duplicates with `Set`
* Error handling using `.catch()`

#### 9. Scroll Animations

* Uses `IntersectionObserver`
* Adds `.visible` class
* Stops observing after trigger

#### 10. Timeline Scroll Animation

* Selects all `.timeline-item` elements
* On `scroll` event, checks if each item's top is within 85% of window height
* Adds `.show` class when in range, removes it when scrolling back up

---

## 6. CSS Architecture

### Theming

* Uses:

```css
body.dark { ... }
```

### Responsive Design

* Uses media queries:

```css
@media(max-width:768px)
```

### Animations

* Uses `transform` and `opacity` transitions
* `max-height` animation for accordion
* `@keyframes gradientMove` for hero name gradient
* `@keyframes spin` for fact loader spinner
* `@keyframes blink` for visit badge dot

---

## 7. Performance Optimizations

* Lazy loading images
* IntersectionObserver instead of scroll events
* Cached DOM elements
* No external libraries
* Efficient CSS transitions
* Reduced unnecessary reflows

---

## 8. Browser Compatibility

Supported in modern browsers:

* CSS Variables
* Fetch API
* IntersectionObserver
* clamp()

---

## 9. Known Limitations

* No backend (form is front-end only)
* API may fail occasionally
* Some modern CSS features have limited support
* Timeline uses a scroll event listener instead of IntersectionObserver, which is slightly less efficient

---

## 10. Summary

This project demonstrates:

* Advanced UI interaction
* State management
* API integration
* Performance optimization

It focuses on building a clean, interactive, and user-friendly experience using only core web technologies.

---