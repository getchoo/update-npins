# update-npins

Update your [npins](https://github.com/andir/npins) sources and create a PR

## Usage

Basic usage is as follows:

> [!NOTE]
> We don't require cachix/install-nix-action specifically, but you
> must install Nix and/or npins yourself before using this action

```yaml
- name: Checkout repository
  uses: actions/checkout@v4

- name: Install Nix
  uses: cachix/install-nix-action@v27

- name: Install npins
  run: nix profile install 'nixpkgs#npins'

- name: Update npins sources
  uses: getchoo/update-npins@v0
```

### Inputs

| Name | Description | Default |
| --- | --- | --- |
| `sources` | A space separated list of sources to update | |
| `npins-directory` | A directory where npins' sources.json and default.nix are located | |
| `commit-message` | A message to use when committing changes (required) | `"npins: update sources"` |
| `author` | The author to use when committing changes | `"github-actions[bot] <github-actions[bot]@users.noreply.github.com>"` |
| `signoff` | Whether to signoff commits | `true` |
| `token` | Token for creating PR (required) | `${{ github.token }}` |
| `pr-branch` | The name of the PR branch created | `"npins-update"` |
| `pr-target` | The target branch of the created PR | |
| `pr-title` | The title of the created PR | `"npins: update sources"` |
| `pr-body` | The body of the created PR | `Automated pull request created by [update-npins](https://github.com/getchoo/update-npins)` |
| `pr-labels` | A comma or newline-separated list of labels to add to the created PR | |

### Outputs

These are re-exports of [peter-evans/create-pull-request](https://github.com/peter-evans/create-pull-request)

| Name | Description |
| --- | --- |
| `pr-number` | The number of the created PR |
| `pr-url` | The URL of the created PR |
| `pr-operation` | The operation performed on the created PR |
| `pr-head-sha` | The HEAD commit SHA of the created PR |

## Special Thanks

Much of this is inspired by [Determinate Systems'](https://determinate.systems/) [update-flake-lock](https://github.com/DeterminateSystems/update-flake-lock) action
