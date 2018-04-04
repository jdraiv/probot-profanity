# Probot: Profanity

> a GitHub App built with [Probot](https://github.com/probot/probot) that marks/censors Issues and Pull Requests containing offensive content.

![mark-demo](https://user-images.githubusercontent.com/25513006/38316149-bc43b3c0-3832-11e8-8b13-53216b342027.png)
![censor-demo](https://user-images.githubusercontent.com/25513006/38316166-c48f9eb8-3832-11e8-95a3-78773c7120a4.png)

Based on @bkeepers's [stale](https://github.com/probot/stale) bot.

## Usage

1. **[Configure the GitHub App](https://github.com/apps/profanity)**
2. Create `.github/profanity.yml` based on the following template
3. It will start scanning for offensive issues and/or pull requests within an hour.

A `.github/profanity.yml` file is required to enable the plugin. The file can be empty, or it can override any of these default settings:

```yml
# Configuration for probot-profanity - https://github.com/nickgarlis/probot-profanity

# Set to true to censor issues (defaults to false)
censor: false

# Placeholder to replace the letters of a forbidden word 
placeholder: '*'

# Number of days of inactivity before an inappropriate Issue or Pull Request is closed.
# Set to false to disable. If disabled, issues still need to be closed manually, but will remain marked as inappropriate.
daysUntilClose: 2

# Issues or Pull Requests with these labels will never be considered inappropriate. Set to `[]` to disable
exemptLabels: []

# Set to true to ignore issues in a project (defaults to false)
exemptProjects: false

# Set to true to ignore issues in a milestone (defaults to false)
exemptMilestones: false

# Label to use when marking as inappropriate
profanityLabel: inappropriate

# Comment to post when marking as profanity. Set to `false` to disable
markComment: >
  This issue has been automatically marked as inappropriate because
  it contains forbidden words. It will be closed if no further edit
  occurs. Thank you for your contributions.

# Comment to post when removing the inappropriate label.
# unmarkComment: >
#   Your comment here.

# Comment to post when closing an inappropriate Issue or Pull Request.
# closeComment: >
#   Your comment here.  

# Limit the number of actions per hour, from 1-30. Default is 30
limitPerRun: 30

# Limit to only `issues` or `pulls`
# only: issues

# Optionally, specify configuration settings that are specific to just 'issues' or 'pulls':
# pulls:
#   markComment: >
#   This issue has been automatically marked as inappropriate because
#   it contains forbidden words. It will be closed if no further edit
#   occurs. Thank you for your contributions.

# issues:
#   exemptLabels:
#     - somelabel
```

## Why did only some issues and pull requests get marked as inappropriate?

To avoid triggering abuse prevention mechanisms on GitHub, only 30 issues and pull requests will be marked or closed per hour. If your repository has more than that, it will just take a few hours or days to mark them all.
