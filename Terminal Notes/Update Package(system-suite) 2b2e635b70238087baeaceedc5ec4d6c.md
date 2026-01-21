# Update Package(system-suite)

Category: Package Management

## Steps

- Edit and push
- then update tar in the system_suite

```bash
cd ~/Developer/Shell/system_suite
git tag <new_version>
git push origin <new_version>
```

- then check the

```bash
curl -L https://github.com/hamim-24/system_suite/archive/refs/tags/<new_version>.tar.gz -o temp.tar.gz
shasum -a 256 temp.tar.gz
rm temp.tar.gz
```

- copy it - `c260a1cdfbb139844a58f16c79546eeddbc9abe8dba9b4494e8d9cf8b3b24b25`
- then go to homebrew-tap

```bash
cd ~/Developer/homebrew-tap
nvim Formula/system-suite.rb
```

- update version, url, sha256 with version

```bash
git add .
git commit -m "version <new_version>"
git push origin main
```

- then uninstall, untap and tap again

```bash
brew uninstall system-suite
brew untap hamim-24/tap
brew tap hamim-24/tap
brew install system-suite
system-suite
```