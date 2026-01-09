/_ WHAT I SAID TO COPILOT _/
Do NOT use CSS-only animations.
This requires JavaScript-based movement and edge collision logic.

I need you to create a clear and precise Markdown plan AND the final implementation.
Please follow the requirements EXACTLY. Do not change the concept.

GOAL
Create a background animation with SMALL OVAL SHAPES that MOVE continuously and BOUNCE when they hit the edges of their container.

STEP 1 – Oval Shapes (IMPORTANT)

- Create small oval shapes (not circles, not blobs).
- Shape style:
  - Small size
  - Oval (border-radius: 50%)
- Use ONLY these colors:
  - Light blue (cyan)
  - Orange
  - Red
  - Green

STEP 2 – Movement and Physics (VERY IMPORTANT)

- The ovals must MOVE continuously across the screen.
- When an oval HITS ANY EDGE of its container, it MUST:
  - Bounce (reverse direction)
  - Continue moving indefinitely
- Movement must be smooth, calm, and constant.
- This should behave like a classic "bouncing DVD logo" or screensaver effect.
- Use JavaScript for movement and collision detection (NOT only CSS keyframes).

STEP 3 – Section Scope (CRITICAL)

- The animation must appear ONLY in:
  - The Hero section
  - The Contact section
- DO NOT show the animation in any other section.
- Each section must have its OWN independent animation instance.

STEP 4 – Number of Ovals

- Hero section: approximately 10 moving ovals
- Contact section: approximately 10 moving ovals

STEP 5 – Background Layering

- The ovals must stay in the BACKGROUND.
- All text, buttons, and content must remain fully visible and clickable above them.
- Use proper positioning and z-index.
- The animation must NOT interfere with scrolling or user interaction.

STEP 6 – Responsiveness and Boundaries

- Ovals must stay INSIDE their section boundaries.
- On resize, the animation should still behave correctly.
- Avoid overflow outside the Hero and Contact sections.

OUTPUT REQUIREMENTS

- First: provide a clear Markdown plan explaining each step.
- Then: provide the full HTML, CSS, and JavaScript code needed.
- The result must visually match a bouncing oval animation like the reference image.

/_ WHAT COPILOT PLANED FOR ME _/

# Plan to Create a Bouncing Oval Background Animation

## STEP 1 – Oval Shapes (IMPORTANT)

- **Goal**: Create small oval shapes with specific styles.
- **Details**:
  - Shape: Oval (not circles or blobs).
  - Size: Small and consistent.
  - Colors: Use only light blue (cyan), orange, red, and green.
  - Styling: Use `border-radius: 50%` to create the oval shape.
- **Implementation**:
  - Use JavaScript to dynamically create and style the ovals.

---

## STEP 2 – Movement and Physics (VERY IMPORTANT)

- **Goal**: Make the ovals move continuously and bounce when they hit the edges of their container.
- **Details**:
  - Movement: Smooth, calm, and constant.
  - Collision: Detect when an oval hits the edge of its container and reverse its direction.
  - Behavior: Similar to a "bouncing DVD logo" effect.
- **Implementation**:
  - Use JavaScript for movement and collision detection.
  - Update positions using `requestAnimationFrame` for smooth animations.

---

## STEP 3 – Section Scope (CRITICAL)

- **Goal**: Display the animation only in the `Hero` and `Contact` sections.
- **Details**:
  - Each section must have its own independent animation instance.
- **Implementation**:
  - Target the `Hero` and `Contact` sections by their IDs.
  - Create separate containers for the ovals in each section.

---

## STEP 4 – Number of Ovals

- **Goal**: Add approximately 10 ovals per section.
- **Details**:
  - Hero section: 10 ovals.
  - Contact section: 10 ovals.
- **Implementation**:
  - Use JavaScript to dynamically generate the ovals for each section.

---

## STEP 5 – Background Layering

- **Goal**: Ensure the ovals stay in the background.
- **Details**:
  - The ovals must not interfere with text, buttons, or user interactions.
  - Use proper `z-index` and positioning.
- **Implementation**:
  - Set the ovals' container to a lower `z-index` than the content.

---

## STEP 6 – Responsiveness and Boundaries

- **Goal**: Ensure the ovals stay within their section boundaries.
- **Details**:
  - The animation must adapt to screen resizing.
  - Prevent ovals from overflowing outside their sections.
- **Implementation**:
  - Use JavaScript to recalculate boundaries on window resize.

---

# Full Implementation

## HTML:

```html
<section id="hero" class="hero">
  <div class="hero-content">
    <h1 class="hero-title">Luna Herrera</h1>
    <p class="hero-subtitle">Portfolio template design</p>
    <a href="#projects" class="btn">View My Work</a>
  </div>
  <div class="oval-container" id="hero-ovals"></div>
</section>

<section id="contact" class="contact">
  <div class="contact-content">
    <h2>Get In Touch</h2>
    <p>Feel free to reach out for collaborations or just a friendly hello!</p>
    <a href="mailto:your-email@example.com" class="btn">Contact Me</a>
  </div>
  <div class="oval-container" id="contact-ovals"></div>
</section>

CSS: /* General styles for oval containers */ .oval-container { position:
absolute; top: 0; left: 0; width: 100%; height: 100%; overflow: hidden; z-index:
-1; /* Ensure ovals stay in the background */ } /* Oval styles */ .oval {
position: absolute; border-radius: 50%; opacity: 0.8; } /* Colors for ovals */
.oval.color-cyan { background: rgb(90, 193, 234); /* Light blue */ }
.oval.color-orange { background: rgb(241, 140, 17); /* Orange */ }
.oval.color-red { background: rgb(255, 87, 87); /* Red */ } .oval.color-green {
background: rgb(144, 238, 144); /* Green */ }
```

JAVASCRIPT:
// Function to create and animate ovals
function createBouncingOvals(containerId, numOvals) {
const container = document.getElementById(containerId);
const colors = ["color-cyan", "color-orange", "color-red", "color-green"];
const ovals = [];

// Create ovals
for (let i = 0; i < numOvals; i++) {
const oval = document.createElement("div");
oval.classList.add("oval", colors[Math.floor(Math.random() * colors.length)]);
oval.style.width = `${Math.random() * 30 + 20}px`; // Random width
oval.style.height = `${Math.random() * 15 + 10}px`; // Random height
oval.style.top = `${Math.random() * 100}%`;
oval.style.left = `${Math.random() * 100}%`;
container.appendChild(oval);

    // Set random speed and direction
    ovals.push({
      element: oval,
      dx: Math.random() * 2 + 1, // Horizontal speed
      dy: Math.random() * 2 + 1, // Vertical speed
    });

}

// Animate ovals
function animate() {
const containerRect = container.getBoundingClientRect();

    ovals.forEach((oval) => {
      const rect = oval.element.getBoundingClientRect();

      // Update position
      let newLeft = rect.left + oval.dx;
      let newTop = rect.top + oval.dy;

      // Check for collisions
      if (newLeft <= containerRect.left || newLeft + rect.width >= containerRect.right) {
        oval.dx *= -1; // Reverse horizontal direction
      }
      if (newTop <= containerRect.top || newTop + rect.height >= containerRect.bottom) {
        oval.dy *= -1; // Reverse vertical direction
      }

      // Apply new position
      oval.element.style.left = `${oval.element.offsetLeft + oval.dx}px`;
      oval.element.style.top = `${oval.element.offsetTop + oval.dy}px`;
    });

    requestAnimationFrame(animate);

}

animate();
}

// Initialize animations for Hero and Contact sections
createBouncingOvals("hero-ovals", 10);
createBouncingOvals("contact-ovals", 10);
