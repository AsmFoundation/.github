# AsmFoundation/.github

The AsmFoundation organization's special repository. GitHub reads two
things from it:

- **[`profile/README.md`](profile/README.md)** is the page shown at
  <https://github.com/AsmFoundation>.
  - **Its banner** is the website's seal in [`profile/assets/`](profile/assets):
    the 1,854 letters of the x86-64 one-byte opcode table, as a ring reading
    FREE OPEN SOURCE ASSEMBLY SOFTWARE around the AsmFoundation A.
    - `seal-print-light.svg` is for light themes, and `seal-print-dark.svg`
      is the same seal on a white rounded card, for dark ones (its ink letters
      would vanish on GitHub's dark background otherwise).
    - Each one stamps the letters in once, as the website's "print" animation
      does (about four seconds), and then stays still. Under reduced motion
      nothing moves.
    - Keep every animation in them finite. Until 2026-11-25 the ring turned
      forever, and the page lagged: a browser redraws an animated image
      whole on every frame, so the turning ring kept about one and a half
      cores of headless Chrome busy for as long as the page stayed open.
      Still, the image costs nothing once the stamp is done.
    - They were drawn from the website's own seal code: every glyph the
      canvas draws was recorded in headless Chrome and written out as SVG
      text, with Archivo and Martian Mono subset and embedded, because an
      image cannot load fonts. If the seal on the website changes, redraw
      them the same way.
  - **The drawing above its project table** is not stored here. It is the
    website's Architecture drawing, which the site build in
    [AsmFoundation/AsmFoundation](https://github.com/AsmFoundation/AsmFoundation)
    writes from `site/data/architecture.json` to
    <https://asmfoundation.github.io/architecture/drawing.svg>. Change it
    there; this page shows the new drawing after the next build.
- **The default community files:** GitHub applies these to every
  repository in the organization that has no file of its own.
  - [`SECURITY.md`](SECURITY.md) is the security policy.
  - [`CONTRIBUTING.md`](CONTRIBUTING.md) is the contribution guide.
