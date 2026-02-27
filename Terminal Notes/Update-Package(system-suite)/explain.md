## File: Update-Package(system-suite).md

- **Purpose**: Checklist for releasing a new version of the `system-suite` project and updating its Homebrew formula.
- **Edit and push**: First, change the code in `system_suite` and push your commits to the repository.
- **Update tarball**: Then ensure a new source tarball is available for the release version.
- **Go to system_suite repo**: `cd ~/Developer/Shell/system_suite` moves into the project directory.
- **Tag new version**: `git tag <new_version>` creates a git tag (e.g. `v1.2.3`) marking the release commit.
- **Push tag**: `git push origin <new_version>` sends the new tag to the remote so GitHub generates archives.
- **Verify tarball and checksum**: The `curl` / `shasum` block downloads the release tar.gz from GitHub, computes its SHA‑256 hash, and then deletes the temporary file.
- **Copy hash**: You copy the printed SHA‑256 hash value to use in the Homebrew formula.
- **Go to homebrew tap**: `cd ~/Developer/homebrew-tap` switches into the Homebrew tap repository.
- **Edit formula**: `nvim Formula/system-suite.rb` opens the Ruby formula for `system-suite`.
- **Update formula fields**: You update the `version`, `url` (pointing to the new tag tarball), and `sha256` (using the copied hash).
- **Stage changes**: `git add .` stages the edited formula file.
- **Commit formula update**: `git commit -m "version <new_version>"` records the formula change with a clear version message.
- **Push to main**: `git push origin main` publishes the updated tap to GitHub.
- **Uninstall old package**: `brew uninstall system-suite` removes the currently installed version.
- **Untap**: `brew untap hamim-24/tap` removes the existing tap so Homebrew will fetch a fresh copy.
- **Retap**: `brew tap hamim-24/tap` re‑adds the updated tap from GitHub.
- **Reinstall**: `brew install system-suite` installs the latest version defined by the updated formula.
- **Run tool**: `system-suite` executes the installed tool to confirm everything works with the new release.

