
```bash
sudo nix-collect-garbage  --delete-older-than 15d
```
|-> Deletes bootloader versions and old nixpkgs 

```bash
nix flake update
```
to update flake dependecis 
