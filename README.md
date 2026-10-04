# homebrew-tap

The Homebrew tap for thruput-io packages.

```sh
brew tap thruput-io/tap
brew trust thruput-io/tap
brew install integration-test-tool
```

## How a formula gets here

Every repository named in `sources.txt` attaches its formulae (`*.rb`) to a
GitHub Release. `publish` takes the latest release of each into `Formula/`,
builds every formula from source and runs its `test do` on a clean macOS
runner, and only then commits to `main`.

It runs when a source tells it there is a release: the source's pipeline
sends a `release` repository dispatch once its integration tests have passed
on `main`. Pull requests here are verified the same way and never published.
It does not run on a schedule or by hand.

## Adding a repository

Add `owner/repo` to `sources.txt`; its pipeline sends the `release` dispatch
after releasing. Its releases must carry `.rb` assets and one
`.tar.gz` asset they build from; `publish` points each formula's `url` at that
asset. `depends_on` names other formulae as `thruput-io/tap/<name>`.
