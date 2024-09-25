name: Pull Request Workflow Cancel Example
on: [pull_request]

jobs:
  hello:
    runs-on: ubuntu-latest
    steps:
      - uses: khan/pull-request-workflow-cancel@1.0.0
        with:
          workflows: "example.yml | second.yml"
        env:
          GITHUB_TOKEN: '${{ secrets.GITHUB_TOKEN }}'
      # Now do whatever other stuff
      - uses: actions/checkout@v2
      - run: echo 'Running now'
      - run: sleep 30
      - run: echo 'wasnt cancelled'
