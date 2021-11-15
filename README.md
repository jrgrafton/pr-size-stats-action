**Note:** this is a hacked prototype on top of https://github.com/pascalgn/size-label-action, use at your own risk :)

# pr-size-stats-action

GitHub action to add a comment to PRs on size statistics for the last 50 PRs in a repo.

## Usage

Create a `.github/workflows/pr-stats-sizes.yml` file:

```yaml
name: size-label
on: pull_request
jobs:
  size-label:
    runs-on: ubuntu-latest
    steps:
      - name: size-label
        uses: "jrgrafton/pr-size-stats-action@v<desired-commit-id>"
        env:
          GITHUB_TOKEN: "${{ secrets.GITHUB_TOKEN }}"
```

## Configuration

The following environment variables are supported:

- `IGNORED`: A list of [glob expressions](http://man7.org/linux/man-pages/man7/glob.7.html)
  separated by newlines. Files matching these expressions will not count when
  calculating the change size of the pull request. Lines starting with `#` are
  ignored and files matching lines starting with `!` are always included.

You can configure the environment variables in the workflow file like this:

```yaml
        env:
          GITHUB_TOKEN: "${{ secrets.GITHUB_TOKEN }}"
          IGNORED: ".*\n!.gitignore\nyarn.lock\ngenerated/**"
```

## License

[MIT](LICENSE)
