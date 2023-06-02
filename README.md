# GitHub Action: Delete older releases

This action deletes older releases of given repo

Add following step to your workflow:

```yaml
- uses: thomashampson/delete-older-releases
  with:
    repo: <owner>/<repoName> # defaults to current repo
    keep_latest: 3
    delete_tag_regex: beta # defaults to ""
    prerelease_only: true # defaults to false
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Available Options

#### `keep_latest`

| required |
| -------- |
| true     |

Specifies number of latest releases (sorted by `created_at`) to keep. Pass `0` if you want to delete all releases

#### `delete_tags`

| required | default |
| -------- | ------- |
| false    | false   |

Specifies whether to delete tags associated to older releases or not. Older tags without any associated releases will not be deleted

#### `repo`

| required | default               |
| -------- | --------------------- |
| false    | repo executing action |

Repo name in the format of `<owner>/<repoName>`. Defaults to the repo that executing this action

#### `delete_tag_regex`

| required | default      |
| -------- | ------------ |
| false    | empty string |

Specifies a pattern to match. If not specified then every release will be targeted. If specified then every release containing the pattern will be targeted. Use this option for example to remove old beta releases.

#### `prerelease_only`

| required | default |
| -------- | ------- |
| false    | false   |

If this is true then only delete prereleases.
