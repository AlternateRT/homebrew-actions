# Setup GPG/SSH Commit Signing GitHub Action

An action that sets up GPG or SSH commit signing.

## Usage

### GPG

```yaml
- name: Set up GPG commit signing
  id: set-up-commit-signing
  uses: Homebrew/actions/setup-commit-signing@master
  with:
    signing_key: ${{ secrets.GPG_SIGNING_KEY }}
```

When committing changes, ensure that the value of the environment variable `HOMEBREW_GPG_PASSPHRASE` is set to the signing key's passphrase.

```yaml
- name: Add and commit changes
  run: |
    git add file.txt
    git commit -m "Updated file.txt"
  env:
    HOMEBREW_GPG_PASSPHRASE: ${{ secrets.GPG_PASSPHRASE }}
```

### SSH

```yaml
- name: Set up SSH commit signing
  id: set-up-commit-signing
  uses: Homebrew/actions/setup-commit-signing@master
  with:
    ssh: true
    signing_key: ${{ secrets.SSH_SIGNING_KEY }}
```
