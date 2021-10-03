# Usage

In your project:

```bash
# use github package registry
cat > .npmrc <<EOF
@thedeveloper:registry=https://npm.pkg.github.com/thedeveloper
EOF
```

```bash
npm i -D \
  @thedeveloper/eslint-config-ts-styleguide \
  @typescript-eslint/eslint-plugin \
  @typescript-eslint/parser \
  eslint-plugin-import \
  eslint
```

Create `.eslintrc.yaml`:
```yaml
env:
  es2021: true
  node: true

parserOptions:
  ecmaVersion: 12
  project: './tsconfig.json'

parser: '@typescript-eslint/parser'

plugins:
  - '@typescript-eslint'

extends:
  - 'plugin:@typescript-eslint/recommended'
  - 'plugin:@typescript-eslint/recommended-requiring-type-checking'
  - '@thedeveloper/eslint-config-ts-styleguide'
```

Add `.vscode/settings.json` to auto fix errors:

```bash
mkdir -p .vscode && \
cat > .vscode/settings.json <<EOF
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
EOF
```
