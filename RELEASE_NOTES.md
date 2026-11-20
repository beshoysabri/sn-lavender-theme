fix: honour the Monospace option, make the opt-ins work, tint the tag label

Four fixes and no colour change: the 90 colour declarations still hash
to the same digest.

The Monospace Font option (Preferences > Appearance) did nothing.
Standard Notes puts .monospace-font on <html> and points .font-editor,
the note editor, at the monospace stack, but section 3's html, body,
body * rule sets Inter with !important and won. A rule after it hands
.font-editor back to the monospace face while the option is on.

The selected tag's label was never lavender on screen. Section 5 set
only color, but Standard Notes paints tag titles with
-webkit-text-fill-color: var(--navigation-item-text-color), which wins,
so the pixels stayed #eeeeee. The rule now sets both, as Lavender Light
and Levanta Dark do.

The section 6 block that turns the -> arrow back off left the arrows
in place. It set only font-variant-ligatures: none, but
--sn-inter-features asks for 'calt' 1, and font-feature-settings
outranks font-variant-ligatures. The block now also takes calt out of
--sn-inter-features, and uses no-contextual so other ligatures stay.

The section 6 block for tabular figures in Super tables stopped at the
<table>: section 3 sets feature settings on every element, so the
cells' text never inherited 'tnum'. It now targets the table and
everything in it.

CI: a check that the Monospace rule is still there.

Checked in app.standardnotes.com: flipping Preferences > Appearance >
Monospace Font draws a note in the monospace face (Chrome's per-node
font report: Liberation Mono, where it was Inter); the uncommented
arrows block leaves "a -> b" as six glyphs in the title and the editor
(five, fused, without it); the selected tag's label samples #a79ef4;
and with the tabular block on, a cell's text computes "cv05", "tnum"
(it was "calt", "cv05", "liga").

Released as 2.6.1.
