# RG35XXH-Store / KNULLI Diagnostics distribution

Public **binary distribution namespace** for the private-source project
[`Tilation/RG35XXH-Store`](https://github.com/Tilation/RG35XXH-Store).

## Channels and paths

- `RG35XXH-Store/development/` — opt-in development updates, signed.
- `RG35XXH-Store/stable/` — signed stable updates.
- The update client expects **public, unauthenticated HTTPS** manifest and
  artifact retrieval. No private GitHub source repository credentials will be
  embedded in the console.

Signed **Development** manifest and ARM64 application artifacts are now published
in [`development/`](development/). They are authenticated only when used with
the trusted P-256 public key pinned in a separately installed bootstrap launcher.
The updater bootstrap is not yet physically validated on KNULLI; do not treat
these artifacts as automatically installable until that validation passes.
A commit or a checksum alone is **not** an authenticated update.

## Distribution boundaries

- Publish only approved ARM64 Native AOT packages, schema-defined signed
  manifests, checksums and non-sensitive release notes.
- Do not copy private source code, workflow secrets, signing private keys,
  GitHub access tokens, hardware-unique identifiers or reports from the
  handheld here.
- Keep the existing binaries on the handheld until a signed candidate is
  downloaded, authenticated, installed to a separate versioned directory and
  successfully launched.
- Maintain the last-known-good release and provide an offline fallback.
- `development` must not silently overwrite a user's `stable` installation.

The full specification is tracked in the private project's [updater issue
#28](https://github.com/Tilation/RG35XXH-Store/issues/28) and signing issue
[#27](https://github.com/Tilation/RG35XXH-Store/issues/27).

**Current status:** Development artifacts are published; Stable releases and a
validated first-install updater package are pending. A signed Development ZIP
is an updater payload, not a stand-alone Ports installer.
