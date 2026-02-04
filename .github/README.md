# nix nario action

![check](https://github.com/spotdemo4/nix-nario-action/actions/workflows/check.yaml/badge.svg?branch=main)

uses [`nix nario`](https://determinate.systems/blog/changelog-determinate-nix-3120/) to save & restore the nix store to the actions cache

chiefly for [`spotdemo4/nix-init`](https://github.com/spotdemo4/nix-init)

## Requirements

[`DeterminateSystems/determinate-nix-action`](https://github.com/DeterminateSystems/determinate-nix-action) or some other way of getting `nix nario`

## Usage

```yaml
- uses: spotdemo4/nix-nario-action/restore@v0.12.3
  id: attic-cache
  with:
    path: nixpkgs#attic-client

# ...

- if: ${{ steps.attic-cache.outputs.cache-hit != 'true' }}
  uses: spotdemo4/nix-nario-action/save@v0.12.3
  with:
    path: nixpkgs#attic-client
```

## Inputs

### `path`

the path to save/restore, defaults to the entire nix store

## Outputs

### `cache-hit` (restore)

whether there was a cache hit
