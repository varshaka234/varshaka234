name: Waka Readme

on:
  # for manual workflow trigger
  workflow_dispatch:
  schedule:
    # runs at 12 AM UTC (5:30 AM IST)
    - cron: "0 0 * * *"

jobs:
  update-readme:
    name: Wakatime DevMetrics
    runs-on: ubuntu-latest
    steps:
      - uses: athul/waka-readme@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          GH_TOKEN: ${{ secrets.GH_TOKEN }}
          SHOW_TITLE: true
          BLOCKS: ->
          TIME_RANGE: all_time
          SHOW_TIME: true
          SHOW_TOTAL: true

                    ### commit
          COMMIT_MESSAGE: Updated wakatime data with new metrics # optional
          TARGET_BRANCH: main # optional
          TARGET_PATH: README.md # optional
          COMMITTER_NAME: github-actions[bot]
          COMMITTER_EMAIL: action-bot@github.com # optional
