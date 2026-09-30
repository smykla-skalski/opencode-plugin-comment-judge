# Publishing to npm

The shared workflow and mise tasks follow the
[organization catalog](https://github.com/smykla-skalski/.github/tree/main/sync).
It runs when a GitHub Release is published, skips prereleases, checks the tag
against `package.json` and `main`, runs `mise run check`, and publishes the
built package with npm OIDC.

## Trusted publisher

The npm trusted publisher for
`@smykla-skalski/opencode-plugin-comment-judge` must name:

| Field | Value |
| --- | --- |
| Repository | `smykla-skalski/opencode-plugin-comment-judge` |
| Workflow filename | `publish.yml` |
| Environment | `npm` |
| Allowed action | Direct `npm publish` |

The old `release.yml` publisher must be replaced before the workflow change is
merged. `NPM_PUBLISH_ENABLED` is already `true`; set it to `false` during the
trust migration, then restore `true` after the new publisher is active.
See [npm trusted publishing](https://docs.npmjs.com/trusted-publishers/).
