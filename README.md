name: GitHub Profile Summary Cards

on:
  workflow_dispatch:

  schedule:
    # 毎日 日本時間 0:00
    - cron: "0 15 * * *"

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Generate profile summary cards
        uses: vn7n24fzkq/github-profile-summary-cards@release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          USERNAME: Ryohei0Otsuka
          BRANCH_NAME: main
          UTC_OFFSET: 9
          AUTO_PUSH: true
          THEME: github_dark
