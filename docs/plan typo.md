/_ WHAT I SAID TO COPILOT _/
Create a clear step-by-step Markdown plan to update my website. Follow the steps in this exact order and explain briefly what files and changes are needed in each step.

STEP 1 – Typography

- Add and apply a custom WOFF font to the entire website.
- The font file is already available (WOFF format).
- Use @font-face in CSS and set it as the main font for the body and headings.

STEP 2 – Navigation Bar Text Alignment

- Update the navigation bar so that all navigation text items are centered horizontally.
- They should no longer be aligned to the left.
- Use modern CSS (Flexbox preferred).

STEP 3 – Navigation Links to Sections

- Make sure each navigation button scrolls to the correct section on the page:
  - "Home" → Home section
  - "About" → About Me section
  - "Projects" → My Projects section
  - "Contact" → Get In Touch section
- Use proper anchor links and section IDs.
- Ensure smooth scrolling if possible.

STEP 4 – Project Cards Layout

- In the "My Projects" section, update the layout so that the project cards appear side by side (horizontally).
- They should no longer stack vertically.
- Use Flexbox or CSS Grid and make it responsive.

After the Markdown plan, provide the necessary HTML and CSS code changes to implement each step.

/_ WHAT COPILOT RESPOND ME _/

# Step-by-Step Plan to Update the Website

## STEP 1 – Typography

- **Goal**: Apply the `Anthony.woff` font to the entire website.
- **Files to Update**: CSS file (e.g., `layout.css` or `main.css`).
- **Changes**:
  - Use `@font-face` to load the `Anthony.woff` font from the `fonts` folder.
  - Set the font as the default for the `body` and all headings (`h1`, `h2`, etc.).

## STEP 2 – Navigation Bar Text Alignment

- **Goal**: Center all navigation text items horizontally.
- **Files to Update**: CSS file (e.g., `layout.css` or `main.css`).
- **Changes**:
  - Use Flexbox to center the navigation items horizontally.
  - Ensure the navigation bar remains responsive.

## STEP 3 – Navigation Links to Sections

- **Goal**: Ensure each navigation button scrolls to the correct section.
- **Files to Update**: HTML file (e.g., `index.html`).
- **Changes**:
  - Add `id` attributes to each section (`Home`, `About`, `Projects`, `Contact`).
  - Update the navigation links to use anchor links (`#id`).
  - Enable smooth scrolling using CSS.

## STEP 4 – Project Cards Layout

- **Goal**: Display project cards side by side in the "My Projects" section.
- **Files to Update**: CSS file (e.g., `layout.css` or `main.css`).
- **Changes**:
  - Use Flexbox or CSS Grid to create a horizontal layout for the project cards.
  - Ensure the layout is responsive, stacking cards vertically on smaller screens.

---

# Code Changes for Each Step

## STEP 1 – Typography

### CSS:

```css
/* filepath: /assets/css/layout.css */
@font-face {
  font-family: "Anthony";
  src: url("../fonts/Anthony.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

body {
  font-family: "Anthony", sans-serif;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "Anthony", sans-serif;
}

/* filepath: /assets/css/layout.css */
.navbar {
  display: flex;
  justify-content: center; /* Center navigation items horizontally */
  align-items: center;
}

.navbar ul {
  display: flex;
  gap: var(--space-md); /* Add spacing between items */
  list-style: none;
  padding: 0;
  margin: 0;
}

.navbar li {
  text-align: center;
}

<!--filepath: /index.html --> <nav class= "navbar" > <ul> <li><a href= "#home"
  >Home</a></li> <li><a href= "#about" >About</a></li> <li><a href= "#projects"
  >Projects</a></li> <li><a href= "#contact" >Contact</a></li> </ul> </nav>
  <section id= "home" > <!-- Home Section Content --> </section> <section id=
  "about" > <!-- About Me Section Content --> </section> <section id= "projects"
  > <!-- My Projects Section Content --> </section> <section id= "contact" >
  <!-- Get In Touch Section Content --> </section>
  /* filepath: /assets/css/layout.css */ html {
  scroll-behavior: smooth; /* Enable smooth scrolling */
}

/* filepath: /assets/css/layout.css */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(
    auto-fit,
    minmax(300px, 1fr)
  ); /* Responsive grid */
  gap: var(--space-lg); /* Add spacing between cards */
}

.project-card {
  background: var(--color-bg-alt);
  border-radius: 16px;
  overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}
```
