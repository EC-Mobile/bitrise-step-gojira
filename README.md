# Bitrise Gojira Step

Automate Jira ticket management based on [Gojira](https://github.com/junkpiano/gojira/)
This provides post CI job task to cleanup/organize jira tickets

## How to use this Step

You must add JIRA information below to secure envs in bitrise secret tab.

- GOJIRA_BASEURL
- GOJIRA_USERNAME
- GOJIRA_PASSWORD

Gojira reads these values.

And add this step as following,

```yaml
- git::https://github.com/EC-Mobile/bitrise-step-gojira.git@1.0.0:
  title: JIRA automation
  inputs:
  - jira_baseurl: "$GOJIRA_BASEURL"
  - jira_username: "$GOJIRA_USERNAME"
  - jira_password: "$GOJIRA_PASSWORD"
  - content: |-
    #!/usr/bin/env bash

    # write your script here
    echo "Hello World!"
    # or run a script from your repository, like:
    # bash ./path/to/script.sh
    # not just bash, e.g.:
    # ruby ./path/to/script.rb
    # ./gojira transition --jql "jql" --action transition_id
    # ./gojira assignee --jql "jql" --reporter
```

On workflow console, you can edit script content. You don't need to write whole script in yaml.
Bitrise transfers dashboard content to yaml automatically.
