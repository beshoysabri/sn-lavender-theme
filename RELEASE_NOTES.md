feat: a charcoal base and lavender selection, instead of near-black

Through 2.5.1 Lavender was native Dark's palette with the accent swapped.
Next to Todoist's dark mode, which wears the same lavender, it felt off,
and the reasons were in the base rather than the accent:

- Near-black (#0f1011) makes a pastel glow. Lavender is 8.0:1 against
  it, where Dark Blue's mid-tone blue was 3.8:1; the native palette was
  tuned for a mid-tone accent.
- There were no in-between lavenders. The 6% accent backdrop is
  invisible on dark, and Standard Notes paints the selected tag and the
  selected note with near-black (#0f1011, and #000000 through the
  contrast background), so selection read as a black bar.
- Sidebar labels and note text were pure #ffffff on near-black, 19.1:1.

2.6.0 lifts the neutrals to charcoal: #1e1e1e base, #252525 sidebar and
surfaces, #2a2a2a borders, #333333 separators, near-opaque charcoal
menus. Pure white softens to #eeeeee (14.4:1). The accent gets
in-between shades: an 18% backdrop, a 35% text-selection wash under
light text (7.1:1) in place of a solid block with dark text, and a 40%
scrollbar thumb. Text on solid lavender follows the base, #1e1e1e at
7.0:1.

A new section 5 makes selection a lavender wash. Standard Notes uses one
colour for hover and selection in both the sidebar and the note list, so
hover stays a neutral grey and rules give the selected tag and the
selected note the 18% backdrop, with the sidebar label in lavender. They
only reference variables, so the digest still covers exactly 90
declarations. The optional extras move to section 6.

Previewed against 2.5.1 in app.standardnotes.com before release. Docs
and the landing page now describe the charcoal base instead of promising
native Dark's colours.

Released as 2.6.0.
