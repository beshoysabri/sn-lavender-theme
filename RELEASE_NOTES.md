feat: Lavender — fork Dark Blue with a #a79ef4 accent

Lavender is Dark Blue v2.4.1 with the accent moved from blue (#086DD6) to
lavender (#a79ef4). Same native Dark foundation, same Inter setup, same
GitHub Pages hosting and pre-publish checks. It gets its own identifier,
com.beshoysabri.lavender-theme, so it installs alongside Dark Blue rather
than replacing it.

The accent family moves together. Info colour, scrollbar thumb, component
highlight, titlebar hover, text-selection background and note-preview
progress go to #a79ef4. The darkened hover shade goes to #8a7ff0 — same
hue, HSL lightness 6.9 points lower, mirroring Dark Blue's #086DD6 →
#065cb5. The 6% backdrop becomes #a79ef40f.

Two values move that Dark Blue left alone: the text that sits on the
accent. Lavender is far lighter than blue, and #eeeeee on #a79ef4 is
2.05:1 — under even the 3:1 large-text floor — so
--sn-stylekit-info-contrast-color and --text-selection-color are now
#0f1011, at 8.02:1. That covers primary buttons, the Daily view's date
tiles and create-note buttons, and selected text. The landing page's
Copy button follows suit.

Accessory tint 1 stays #086dd6. It is a native Dark default for icon
tints, not the accent.

CI: the colour digest is re-baselined to the lavender palette — still 90
declarations, still everything except the three --sn-inter-* knobs.

Docs: README, landing page, ext.json, package.json and deploy.sh repointed
at sn-lavender-theme. Two stale "section 4" references to the opt-in
blocks now say section 5, where they have lived since v2.4.0.

Released as 2.5.0.
