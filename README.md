# homebrew-tap

Homebrew tap for the Pewter command-line client, from Heir Pte Ltd.

```sh
brew install omegacomputes/tap/pewter
```

That is shorthand for `brew tap omegacomputes/tap` followed by `brew install pewter`. It installs `pewter` and its
short alias `pew`, plus shell completions for bash and zsh.

- Source for the CLI: <https://github.com/OmegaComputes/pewter> (Apache License 2.0)
- Website: <https://omegacompute.com>
- Security issues: see `SECURITY.md` in the CLI repository, or write to devs@h3ir.com

## How the formula is trusted

Release archives are served from `https://omegacompute.com/cli/`. The formula pins the SHA-256 of each archive.
Those hashes are copied from `SHA256SUMS` only after its Ed25519 signature has been verified against the
release public key. Homebrew itself checks the SHA-256, not the signature.

Each archive contains `pewter`, `LICENSE` and `NOTICE`. The formula installs the binary, the `pew` symlink and
completions, and puts `LICENSE` and `NOTICE` in the package's doc directory.

## Status

Not live yet. The formula (`Formula/pewter.rb`) is added with the first signed release, once real, verified
hashes exist. Until then `brew install` will not work.

## Maintainers: updating the formula

1. Publish the signed release and verify `SHA256SUMS.sig` (steps in `RELEASING.md` in the CLI repository).
2. From a `pewter` checkout, generate the formula:
   `packaging/homebrew/update-formula.sh X.Y.Z /path/to/SHA256SUMS --i-verified-the-signature > Formula/pewter.rb`
3. Check it: `brew audit --strict --new --online omegacomputes/tap/pewter` and `brew install --build-from-source omegacomputes/tap/pewter`, then `brew test pewter`.
4. Commit and push to `main` of this repository.

Never commit hashes you have not verified. Never commit a release private key to this repository.

## License

Apache License 2.0. See [LICENSE](LICENSE).
