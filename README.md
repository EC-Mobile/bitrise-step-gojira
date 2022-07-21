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
- git::https://github.com/EC-Mobile/bitrise-step-gojira.git@1.1.0:
  title: JIRA automation
  inputs:
  - jira_baseurl: "$GOJIRA_BASEURL"
  - jira_username: "$GOJIRA_USERNAME"
  - jira_password: "$GOJIRA_PASSWORD"
  - content: |-
    #!/usr/bin/env bash

    # ./gojira transition --jql "jql" --action transition_id --comment "updated by bot"
    # ./gojira assignee --jql "jql" --reporter
```

You can also input information on bitrise workflow console.

### gojira command locations

- `${PWD}/gojira` (current directory)
- `/usr/local/bin/gojira` (system wide)

You can access gojira in both ways,
`./gojira` or `gojira`.
