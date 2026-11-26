# xping-dev/docs

Source of https://docs.xping.io: product documentation for the Xping CLI, its CI integrations
(GitHub Action, GitLab component, Azure DevOps task) and the Xping SDK.

## Build

```sh
dotnet tool restore
./scripts/import-reference.sh "$(cat xping-version.txt)"   # reference pages + schemas from xping-dev/xping
dotnet docfx docfx.json --serve                # http://localhost:8080
```

## What lives where

| Content | Owner | How it gets here |
|---|---|---|
| Guides, CI setup, concepts | this repo | written here |
| Exit codes, release verification, command reference, rule pages, `.xping.yml` reference | `xping-dev/xping` (`docs/reference/`) | `scripts/import-reference.sh <tag>`, never edited here |
| `session.schema.json`, `history.schema.json` | `xping-dev/xping` (`schema/`) | same script, published under `/schema/` |
| SDK guides (`sdk/`) | moved from `xping-dev/sdk-dotnet@dc64c02` (`docs/`) | edited here from now on. The Cloud and 1.0.0-rc CLI parts carry notes until the SDK drops them. |

Pages generated from code are imported at the release tag in `xping-version.txt`, so the site always describes a released version. Bump the file to publish docs for a new release. Until the first release (`v2.0.0-alpha.1`) it names `main`.

## Old URLs

docs.xping.io used to serve the SDK site from xping-dev/sdk-dotnet. The paths released packages
link (for example `/getting-started/quickstart-nunit.html`, `/configuration/configuration-reference.html`,
`/known-limitations.html`, `/cli/command-reference.html`, `/api/...`) are redirect pages
(`redirect_url` front matter) at their old locations. Keep them.

