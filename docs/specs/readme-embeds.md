# README Embed Invariants

- When adding a remote image to a README, verify that its public URL returns `200` with an image content type before publishing. Violation: GitHub renders a broken-image placeholder.
- Do not use tokenless Star History live charts. GitHub's stargazer-history restrictions and Star History rate limits make them unreliable for public READMEs.
- Prefer a GitHub Stars badge from Shields for a stable, public, credential-free call to action.
