# cargo-vendor-checksum
It is a tool to update checksums of modified files in vendor directory, e.g.
when patching sources for building packages. One can specify files via
`--files-in-vendor-dir` flag or run batch process via `--all` or `--packages`

NOTE! Batch process will remove references of missing files from
'.cargo-checksum.json'

## Examples
If you already in the package catalog.

Specify files you need to update checksums:
```
cargo-vendor-checksum --files-in-vendor-dir nix/src/net/mod.rs nix/Cargo.toml
```
Update checksum of all vendored files via batch process (this command could
take a lot of time to complete):
```
cargo-vendor-checksum --all
```
Specify vendored packages for batch processing:
```
cargo-vendor-checksum --packages anyhow nix
```
Set the path of `vendor` directory if you are not in the repository catalog:
```
cargo-vendor-checksum --vendor $PWD/hyperfine/vendor -f nix/src/net/mod.rs
```
