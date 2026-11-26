# Contributing to hobnix/community

How to submit a package is in [README.md](README.md). This page is about the terms.

## Two licences, kept apart

- **This repository's own files** (index tooling and CI, README, policy, manifests) are under the [MIT licence](LICENSE). A manifest you add
  is one of those files: by opening the pull request you offer it under MIT.
- **Your package** stays in your own repository under the licence you chose (it must be one of the licences in `policy.toml`, and the
  package folder carries its `LICENSE`). Listing it here does not change that licence, and this repository holds no copy of your code.

## Sign off your commits

Sign off every commit personally with `git commit -s`. That adds a `Signed-off-by:` line and means you agree to the
[Developer Certificate of Origin](https://developercertificate.org/): you wrote the change or have the right to submit it under the licence
above. Use your real name and an email git can attribute to you.

- This applies to AI-assisted work too. The sign-off is yours, whoever or whatever helped write the change.
- An AI tool never adds a sign-off, in nobody's name. Do not let one do it for you.
- Forgot it on the last commit: `git commit --amend -s --no-edit`.
- No check enforces this yet (hobnix/core#1287); a maintainer asks for it in review.

## Review

A maintainer reviews every pull request. A refused pin (size, licence, host, name, version not raised) fails the `index` run before that.
Verified is not an audit of every line: read what a package asks for before you install it.
