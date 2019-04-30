# Revision history for obelisk

This project's release branch is `master`. This log is written from the perspective of the release branch: when changes hit `master`, they are considered released, and the date should reflect that release.

## Unreleased

* Fix crashes of Android apps on 32-bit ARM devices.
* Provide a way to indicate acceptance of the Android SDK license by passing `config.android_sdk.accept_license = true;` in the arguments to the import of `.obelisk/impl` in the project's `default.nix`.
* Add `COMPLETE` pragma to `(:/)`. Using this pattern synonym should no longer generate spurious warnings about non-exhaustive pattern matching.
* Make asset path hashing strict (see `Obelisk.Asset.Gather`)
* Add the `ob shell` command to enter a nix shell for an obelisk project
* Removed `MonadIO` from `ObeliskWidget` to prevent accidental IO during prerendering. If you need to do IO in a widget it should be on the right hand side of a `prerender`.
* Significantly changed the interface to the "executable config" packages. `obelisk-executable-config-lookup` is a new internal package which looks up all configs in a platform-specific way. `obelisk-executable-frontend` and `obelisk-executable-backend` provide MTL-style monad classes (`HasFrontendConfigs` and `HasBackendConfigs`) which the frontend and backend, repsectively, can use to look up configs. This replaces the old `get` function which ran in `IO`.

## v0.1.0.0 - 2019-03-29

* Use reflex-dom's `HydrationDomBuilder` to "hydrate" statically rendered DOM served by the Obelisk backend (rather than re-creating DOM and replacing it all).
* Add `HasCookies` and `CookiesT` to allow `ObeliskWidget`s to access cookies during static and "hydrated" DOM rendering.
