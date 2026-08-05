# Brand assets

| File | Use |
|---|---|
| `hero.svg` | The README hero. Used here via a relative path. |
| `hero.png` | 1440x504. For npm, which needs an absolute URL. |
| `pixel-mark.svg` | The current mark, 8 cells, green `#34C759`. |
| `marks/*.png` | Agent logos for the "works with" row. |

## Rules these follow

The hero is built from the **current** design tokens: a gradient field (dark with
depth, never flat `#000`), the PixelMark, a Geist-first sans stack, green as the
one accent, and monospace **only** inside the command chip, because a command is
genuine code.

Do not reuse the `aethereum-launch-video` asset suite here. It is the retired
brand language: the wordmark is the `</aethereum>` string set in monospace on flat
black, and the poster is green ASCII art. Those predate the 2026-08-03 premium-dark
direction, which retired the terminal aesthetic, flat black, and monospace outside
code. The site's own `/opengraph-image` is stale in the same way and should not be
used as a hero until it is regenerated.

## Two traps, both measured

**`--` is illegal inside an XML comment.** The first draft of `hero.svg` had
`--bg-field-top` in a comment and was invalid XML. Browsers shrugged; strict
parsers rejected it. Validate with a real XML parser, not by opening it in a
browser.

**A correction to an earlier note in this repo's history:** a commit message here
claims `raw.githubusercontent.com` serves `.svg` as `text/plain`. That is wrong,
and measured: it serves `image/svg+xml`, so an SVG *can* be an `<img>` source off a
raw URL. `hero.png` still exists for npm, but for the real reason, which is that
**npm sanitizes SVG in rendered READMEs** and a raster hero is the reliable choice
there. GitHub renders both.
