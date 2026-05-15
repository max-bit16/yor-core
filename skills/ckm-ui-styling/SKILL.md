# ckm-ui-styling

Refine UI styling across buttons, cards, forms, and interactive states.

Buttons:
- Primary: accent background, white text, padding 12px 24px, border-radius 6px, hover: darken 10%
- Secondary: transparent background, accent border, accent text, same padding
- Ghost: no border, accent text, hover: accent background at 10% opacity

Cards:
- Border: 1px solid with low-opacity accent or neutral
- Padding: 24px minimum
- Hover: translateY(-2px) + border-color to accent, transition 200ms

Forms:
- Input height: 44px minimum
- Border: 1px solid neutral, focus: accent color, transition 150ms
- Label: always visible (never placeholder-only)
- Error state: red border + error message below field

All hover states use transition: 150–200ms ease.
