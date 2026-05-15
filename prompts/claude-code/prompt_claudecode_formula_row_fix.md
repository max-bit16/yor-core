In styles.css, find the formula-row separator rule that uses
var(--hairline) as border-bottom color.

Add a targeted selector for the dark middle row only:

.formula-row.formula-row--dark {
  border-bottom-color: rgba(255, 255, 255, 0.12);
}

If the dark middle row uses a different class or attribute,
run a grep first to find the exact selector:

grep -n "formula-row" styles.css pages-core.jsx

Then apply the fix to the correct selector.
Do not change any other formula-row styles.
