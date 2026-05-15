In styles.css, find the .comp-hero-bg::before rule.

Increase the opacity value until the background images are
clearly visible while keeping the text readable.

Current value: opacity: 0.18

Apply this change:

.comp-hero-bg::before {
  opacity: 0.35;
}

Then add a dark scrim overlay directly on .comp-hero-bg to
preserve text contrast:

.comp-hero-bg::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    rgba(15, 30, 50, 0.45) 0%,
    rgba(15, 30, 50, 0.25) 50%,
    rgba(15, 30, 50, 0.55) 100%
  );
  z-index: 0;
  pointer-events: none;
}

Verify that .comp-hero-bg > * has z-index: 1 so all content
sits above both the image and the scrim.

Check each competence page: image must be clearly visible,
headline text must remain fully readable (white on dark).
If contrast is insufficient, increase the scrim opacity by
0.1 increments. If the image is still too subtle, increase
the ::before opacity to 0.45 maximum.
