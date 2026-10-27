# GitHub Stats

This repository generates GitHub profile statistics with the Zig implementation
from [jstrieb/github-stats](https://github.com/jstrieb/github-stats). The workflow
runs daily and can also be started manually.

Only non-fork repositories owned by the authenticated user are used for
repository statistics. Public and permitted private repositories are included.
Private repositories are never cloned; if GitHub does not return contributor
statistics, their changed-line counts may be incomplete. As in upstream, the overall contribution counts come from
GitHub's user contribution collection and may include contributions outside
those repositories. Public repositories are discovered from commit contributions; private repositories
are discovered directly from repository metadata.

## Setup

1. Create a fine-grained personal access token with access to the desired
   repositories and **Metadata: read-only**. No code access or repository write
   permissions are needed. Optionally,
   grant the account permission **Email addresses: read** to improve attribution
   when contribution statistics are calculated from Git history. Without it,
   GitHub noreply addresses are used as a fallback.
2. Save the token as the `ACCESS_TOKEN` Actions repository secret.
3. Start **Generate Stats Images** under Actions. The generated images are saved
   in `generated/` on the `master` branch. The workflow uses its separate,
   repository-scoped `GITHUB_TOKEN` to commit those images.

Optional existing secrets `EXCLUDED` and `EXCLUDED_LANGS` exclude comma-separated
repository names and languages. Review upstream's documentation for general
limitations and details about the generated statistics.

```md
![Overview](https://raw.githubusercontent.com/e-feit/github-stats/master/generated/overview.svg)
![Languages](https://raw.githubusercontent.com/e-feit/github-stats/master/generated/languages.svg)
```
