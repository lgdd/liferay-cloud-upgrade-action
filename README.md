# Liferay Cloud Upgrade Action

GitHub Action to create a new branch and pull request if a new versions for Liferay Cloud Docker images are available.

If you're looking for the same action but for Liferay upgrade, take a look at this: https://github.com/lgdd/liferay-upgrade-action

## Requirements

This action create a branch, push changes and create a pull request. So make sure to give proper permissions to GitHub Actions in your repository:

- Go to `Settings > Actions > General > Workflow Permissions`
- Select `Read and write permissions`
- Check `Allow GitHub Actions to create and approve pull requests`

More information in [GitHub Actions documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-the-default-github_token-permissions).

## Usage

You can use this action in a [GitHub Actions Workflow](https://help.github.com/en/articles/about-github-actions) by a adding a YAML file under `.github/workflows/` with the following content:

```yaml
name: liferay-cloud-auto-upgrade
run-name: Liferay Cloud Auto Upgrade

on:
  schedule:
    # https://crontab.guru/every-night-at-midnight
    - cron: '0 0 * * *'

permissions:
  contents: write
  pull-requests: write

jobs:
  liferay-cloud-upgrade:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: lgdd/liferay-cloud-upgrade-action@v1
```

## License

[MIT](LICENSE)
