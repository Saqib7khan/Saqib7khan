<img align="left" width="47%" src="https://github-readme-stats.vercel.app/api?username=Saqib7khan&show_icons=true&theme=radical" />
<img align="left" width="47%" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Saqib7khan&layout=compact" />

name: Latest blog post workflow
on:
  schedule: # Run workflow automatically
    - cron: '0 * * * *' # Runs every hour, on the hour
  workflow_dispatch: # Run workflow manually (without waiting for the cron to be called), through the GitHub Actions Workflow page directly
permissions:
  contents: write # To write the generated contents to the readme

jobs:
  update-readme-with-blog:
    name: Update this repo's README with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Pull in dev.to posts
        uses: gautamkrishnar/blog-post-workflow@v1
        with:
          feed_list: "https://mohdsaqibkhan379.medium.com/feed"
