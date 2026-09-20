# Feed update log (master record)

Every change to this feed **must** append a row here and then run
`scripts/feed-verify.sh` — the verifier fails if a project index changed
after the log was last updated. Rows are newest first. The `Verified` column
means the update was re-checked after push (signature, checksums, index
integrity) by `scripts/feed-verify.sh` or an equivalent manual check.

| Date (UTC) | Project | Version | Action | Verified |
|---|---|---|---|---|
| 2026-09-20 | wificalling-location-gateway | 1.4.0-r17 | compliant release: WLOC/WFC decoupling (manual WLOC independent of the gateway, auto mode read-only exit follow), control-plane starvation fix, WFC device IPv6 through the tunnel + WLOC IPv6 guard fix, per-channel tunnel status in the monitor, carrier line-compatibility notes from live AX6S testing; standard + lite, x86_64 + aarch64 (apk for 25.x on the GitHub release), signed index | ✅ |
| 2026-09-15 | wificalling-location-gateway | 1.3.0-r16 | compliant release: audit hardening (fail-open route lifecycle, daemon control-plane worker thread, LuCI/build fixes, rustls 0.23.45); six assets, signed index | ✅ |
| 2026-09-14 | wificalling-location-gateway | 1.3.0-r15 | compliant release: shadowsocks node support (PR #102); six assets, signed index | ✅ |
| 2026-09-14 | wificalling-location-gateway | (withdrawal) | v1.3.0-r14 marked prerelease and withdrawn from the feed (unmerged PR #98, IPv6-coexistence reversal not adopted); index restored to the compliant v1.3.0-r13 packages | ✅ feed-verify |
| 2026-08-30 | (repository) | — | renamed to `Smthdagg-Repo-feeds`; restructured to per-project directories (`wificalling-location-gateway/` holds the packages, 8 project dirs reserved); added `scripts/feed-verify.sh`; router feed URL migrated to the `wificalling-location-gateway/` subdirectory | ✅ feed-verify |
| 2026-08-29 | wificalling-location-gateway | 1.3.0-r13 | realistic memory gate (computed need + self-heal retry); standard + lite, x86_64 + aarch64 | ✅ |
| 2026-08-29 | wificalling-location-gateway | 1.3.0-r12 | auto-save applied manual locations; standard + lite, x86_64 + aarch64 | ✅ |
| 2026-08-29 | wificalling-location-gateway | 1.3.0-r11 | LuCI error-path hardening; standard + lite, x86_64 + aarch64 | ✅ |
| 2026-08-29 | wificalling-location-gateway | 1.3.0-r10 | audit hardening (upstream-map lifecycle, probe without curl); standard + lite, x86_64 + aarch64 | ✅ |
| 2026-08-29 | wificalling-location-gateway | 1.3.0-r9 | WLOC fail-open and low-memory node health; standard + lite, x86_64 + aarch64 | ✅ |
| 2026-08-24 | wificalling-location-gateway | 1.3.0-r1 | publish package source (standard + lite, x86_64 + aarch64; apk for 25.x) | ✅ |
| 2026-08-19 | wificalling-location-gateway | 1.2.2 | reject xhttp (sing-box unsupported) | ✅ |
| 2026-08-19 | wificalling-location-gateway | 1.2.2 | grpc/httpupgrade transport import fix | ✅ |
| 2026-08-19 | wificalling-location-gateway | 1.2.2 | monitor debounce, canonical version | ✅ |
| 2026-08-19 | wificalling-location-gateway | 1.2.2 | log clear via rpcd truncate | ✅ |
