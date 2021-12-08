# action-slack-notification
A [GitHub Action](https://github.com/features/actions) to send a message to a Slack channel.


## Example usage

Here is an example setup of this action:

```yml
name: Some Action

on:
  workflow_dispatch:
  
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
        ...
          steps before
        ...  
        
      - name: Slack Notification
        uses: AndyKIron/slack-notify@main
        with:
          channel: some-slack-channel
          username: sender-name
          message: "tour message here"
          slack_webhook: ${{ secrets.SLACK_WEBHOOK }}

        ...
          steps after
        ...


```

### Inputs (with)

| Variable      |          | Purpose                                                                                                                                       |
|---------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| channel       | required | Slack channel name where you want sending message                                                                                             |
| username      | required | Message sender name                                                                                                                           |
| icon_url      | optional | Message Icon default: https://avatars.githubusercontent.com/t/5433436?s=32&v=4                                                                |
| status        | optional | Message status (left border color). Values - good (green), warning (yellow), danger (red), or any hex color code (eg. #439FE0). Default - good |
| message       | required | Message content like `"<!channel> :rotating_light: *${{github.actor}}* do some wrong!"` (markdown supported)                                     |
| slack_webhook | required | You can [generate a Slack incoming webhook token from here](https://slack.com/apps/A0F7XDUAZ-incoming-webhooks).                              |


- Create `SLACK_WEBHOOK` secret using [GitHub Action's Secret](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets#creating-encrypted-secrets-for-a-repository).
