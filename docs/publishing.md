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

Publishing is disabled with `NPM_PUBLISH_ENABLED=false` while the npm trusted
publisher still names the old `release.yml` workflow. Replace that publisher
with the connection above, then restore `NPM_PUBLISH_ENABLED=true`.
See [npm trusted publishing](https://docs.npmjs.com/trusted-publishers/).
