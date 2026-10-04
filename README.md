# brew

The Homebrew tap for thruput-io packages.

```sh
brew tap thruput-io/brew https://github.com/thruput-io/brew
brew install integration-test-tool
```

## How a formula gets here

Every repository named in `sources.txt` attaches its formulae (`*.rb`) to a
GitHub Release. `publish` takes the latest release of each into `Formula/`,
builds every formula from source and runs its `test do` on a clean macOS
runner, and only then commits to `main`.

It runs every hour, on a push to `main`, on pull requests (without
publishing), and by hand from the Actions tab.

## Adding a repository

Add `owner/repo` to `sources.txt`. Its releases must carry `.rb` assets whose
`url` is a release asset and whose `depends_on` names other formulae as
`thruput-io/brew/<name>`.
