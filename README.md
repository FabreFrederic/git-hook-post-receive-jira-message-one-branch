#post-receive hook

post-receive hook

Add comments in the Jira tickets using Jira API.
When the git push is received, every commit adds a comment depending on the Jira tickets found in the commit message.
The script posts a message to Slack in a specific channel too.

This script sends comments only for commits pushed on the branch whose name is $branchName.
If several jira tickets are found in the git commit message, the same comment is send to every Jira tickets
The Jira comment contains :
- SHA1 commit
- Commit author
- Commit date
- Commit message
- A link to your git service website of the commit if gitServiceRootUrl is not empty

This file must be named post-receive, and be saved in the hook directory in a bare git repository.
Run "chmod +x post-receive" to make it executable.

Don't forget to change
- Branch name to filter (this is mandatory)
- Jira server urls
- Jira id regex
- Jira role name to filter the visibility of the comments in Jira
- Jira login
- Jira password
- git service url
- Slack config, and import a git icone into Slack

Don't forget to install jshon
In order to parse jira message and to use this message in a curl command : you have to install jshon
https://github.com/keenerd/jshon
