# How to release

## Prepare

- Update `CHANGELOG.md`
- Bump version in `Cargo.toml` and `cargo build --release`
- Commit new version
- Create tag for version
- Push commit and tag

## Publish

- `cargo publish`
- Run [`cargo aur`](https://crates.io/crates/cargo-aur)
  - Go to repository for [i3-back-bin (AUR)](https://aur.archlinux.org/packages/i3-back-bin)
  - Copy `PKGBUILD`
  - Generate `.SRCINFO`: `makepkg --printsrcinfo > .SRCINFO`
  - Commit new version
- Run [`cargo deb`](https://crates.io/crates/cargo-deb)
  - To run inside Docker container: `docker run -it -v .:/app rustlang/rust:nightly bash`, `cargo install cargo-deb`, `cd /app && cargo deb`

## Release

- Create GitHub release with changelog
- Add the following files to the GitHub release:
  - `target/release/i3-back`
  - `target/debian/i3-back_*.deb`
  - `i3-back-*.tar.gz`
- Push AUR repository
