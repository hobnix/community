# hobnix/community

Community packages for Hobnix servers. This repository holds no code: each package is a small **manifest** in `manifests/` that pins one commit of a
package folder in your own repository. A CI job fetches the pinned commit, checks it against `policy.toml`, builds a signed index and publishes it.

## Submit a package

1. Put your package (a folder with `package.toml` and `LICENSE`) in a public repository on an allowed host (see `policy.toml`).
2. Open a pull request that adds `manifests/<name>.toml`. `<name>` is a lowercase word, the same as `name` in your `package.toml`, and not already
   used in the official index.

   ```toml
   name = "mypackage"
   kind = "recipe"                                  # recipe, extension or blueprint
   source = "https://github.com/you/your-repo"      # https, no login, no port
   commit = "<full 40-character commit hash>"
   path = "packages/mypackage"                      # folder inside the repository ("." for the root)
   tree = "<tree hash of that folder>"
   license = "MIT"                                  # one of the licences in policy.toml
   maintainers = ["your-github-name"]
   status = "active"
   ```

3. The job summary of the `index` run shows what the pin does. A refused pin (size, licence, host, name, version not raised) fails the run.
4. A maintainer reviews the pull request. After the merge the push or daily run signs and publishes the index.

To release a new version: raise `version` in your `package.toml`, push, and open a pull request that changes `commit` and `tree`.

Community packages are not reviewed line by line: read what a package asks for (permissions) before you install it.

## Tiers: Official, Verified, Community

- **Official**: `hobnix/official`, signed with a key shipped in the core.
- **Verified**: this repository. A maintainer reviewed the pull request that pins the commit, and CI signs the index (https://packages.hobnix.dev/community). A new commit is a new review. Verified is not an audit of every line.
- **Community**: any other repository a user adds with `hs pkg repo add <index-url>`, signed with its own key, shown as Unverified.

Details: docs/PLAN-registry.md in https://github.com/hobnix/core. The index is published and answers today but lists no package yet. Not tested on hardware yet: installing a community package on a server.

## Maintainers

`.github/` and `policy.toml` are owned by the maintainers (`.github/CODEOWNERS`): a pull request runs its own copy of both. Not tested on hardware yet.
