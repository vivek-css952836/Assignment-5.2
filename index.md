<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 5.2 - CSS Selectors Practice</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <!-- Specific section styled with ID selector -->
  <header id="main-header">
    <h1>Web Development Course</h1>
    <p class="subtitle">CSS Selectors Practice Assignment</p>
  </header>

  <main>
    <section>
      <h2>Learning Modules</h2>
      
      <!-- Cards styled using Class selector -->
      <div class="card">
        <h3>Module 1: HTML Basics</h3>
        <p>Learn structural tags, attributes, semantic elements, and text formatting.</p>
      </div>

      <div class="card">
        <h3>Module 2: CSS Styling</h3>
        <p>Explore selectors, the box model, flexbox layout, and cascading rules.</p>
      </div>

      <div class="card">
        <h3>Module 3: JavaScript</h3>
        <p>Understand variables, functions, event handling, and DOM manipulation.</p>
      </div>
    </section>

    <section>
      <h2>Assignment Instructions</h2>
      <p>Follow the guidelines carefully and submit your code files along with the written explanation.</p>
    </section>
  </main>

  <!-- Element demonstrating specificity and cascade conflict -->
  <footer id="footer-note" class="highlight-box">
    <p>Submit your assignment on time!</p>
  </footer>

</body>
</html>

File 2: styles.css

/* ==========================================
   1. Universal Selector (*)
   Applies a global CSS reset for margins/padding
   ========================================== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Base Body Styling */
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  background-color: #f4f6f8;
  color: #333;
  padding: 20px;
}

/* ==========================================
   2. Grouping Selector
   Styles multiple heading elements simultaneously
   ========================================== */
h1, h2, h3 {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #1a252f;
  margin-bottom: 10px;
}

/* ==========================================
   3. Element Selector
   Styles all paragraph elements globally
   ========================================== */
p {
  color: #555;
  font-size: 1rem;
  margin-bottom: 8px;
}

/* ==========================================
   4. Class Selector (.card)
   Styles multiple reusable module card containers
   ========================================== */
.card {
  background-color: #ffffff;
  border-left: 4px solid #3498db;
  border-radius: 6px;
  padding: 16px;
  margin-bottom: 15px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
}

/* ==========================================
   5. ID Selector (#main-header)
   Styles a unique header section
   ========================================== */
#main-header {
  background-color: #2c3e50;
  color: #ffffff;
  padding: 25px;
  text-align: center;
  border-radius: 8px;
  margin-bottom: 25px;
}

/* Direct child paragraph override within header */
#main-header p {
  color: #ecf0f1;
}

/* ==========================================
   6. Conflicting CSS Rules (Cascade & Specificity Test)
   ========================================== */

/* Rule A (Lower Specificity): Class Selector */
.highlight-box {
  background-color: #e74c3c; /* Red */
  color: #ffffff;
  padding: 15px;
  text-align: center;
  border-radius: 6px;
  margin-top: 20px;
}

/* Rule B (Higher Specificity): ID Selector */
#footer-note {
  background-color: #27ae60; /* Green */
}
File 3: explanation.md (Short Explanation)

# Explanation of CSS Selectors & Cascade

## 1. Universal Selector (`*`)
* **Usage:** `* { margin: 0; padding: 0; box-sizing: border-box; }`
* **Purpose:** Selects every element on the DOM tree to remove default browser margins and paddings, ensuring consistent cross-browser layout behavior.

## 2. Grouping Selector (`h1, h2, h3`)
* **Usage:** `h1, h2, h3 { font-family: ...; }`
* **Purpose:** Combines multiple selectors separated by commas to apply the same font-family and text properties across all headings, keeping the CSS code DRY (Don't Repeat Yourself).

## 3. Element Selector (`p`)
* **Usage:** `p { color: #555; }`
* **Purpose:** Targets every HTML `<p>` element directly by its tag name to set a standard font size and line height.

## 4. Class Selector (`.card`)
* **Usage:** `.card { background-color: #ffffff; ... }`
* **Purpose:** Targetable reusable class name prefixed with a dot (`.`). Applied to multiple module `<div>` containers so they share identical card-like visual styles.

## 5. ID Selector (`#main-header`)
* **Usage:** `#main-header { background-color: #2c3e50; ... }`
* **Purpose:** Targets a unique HTML element on the page using its `id` attribute, prefixed with a hash (`#`). Ideal for top-level structural elements like the main header.

---

## 6. CSS Cascade & Specificity Observation

In the stylesheet, two conflicting rules target the footer element:
1. `.highlight-box { background-color: #e74c3c; }` (Class Selector - Specificity score: `0,0,1,0`)
2. `#footer-note { background-color: #27ae60; }` (ID Selector - Specificity score: `0,1,0,0`)

### Observation Result:
The footer background rendered as **Green (`#27ae60`)** instead of Red (`#e74c3c`).

### Why it happened:
In CSS, when conflicting styles apply to the same element, the browser uses **Specificity** rules to determine which style takes precedence:
* **ID Selectors** have higher specificity weight than **Class Selectors**.
* Even if `.highlight-box` were written below `#footer-note` in the CSS file, the ID selector would still win due to its higher specificity weight.