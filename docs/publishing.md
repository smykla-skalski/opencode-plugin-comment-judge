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

Set the repository variable `NPM_PUBLISH_ENABLED=true` for direct publishing.
Other values run `npm publish --dry-run`. Keep the trusted publisher aligned
with the fields above.
See [npm trusted publishing](https://docs.npmjs.com/trusted-publishers/).
