# Jira Edit
Edit issue

For examples on how to use this, check out the [gajira-demo](https://github.com/atlassian/gajira-demo) repository
> ##### Only supports Jira Cloud. Does not support Jira Server (hosted)

## Usage

> ##### Note: this action requires [Jira Login Action](https://github.com/marketplace/actions/jira-login)

```yaml
- name: Edit
  id: edit
  uses: dailymotion/gajira-edit@main
  with:
    issue: 1234
    project: GA
    issuetype: Build
    summary: |
      Build completed for ${{ github.repository }}
    description: |
      Compare branch
    fields: '{"customfield_10171": "test"}'

- name: Log edited issue
  run: echo "Issue ${{ steps.edit.outputs.issue }} was edited"
```

----
## Action Spec:

### Environment variables
- None

### Inputs
- `issue` (required) - issue key to perform an edit
- `project` (required) - Key of the project
- `issuetype` (required) - Type of the issue to be edited. Example: 'Incident'
- `summary` (required) - Issue summary
- `description` - Issue description
- `fields` - Additional fields in JSON format

### Outputs
- `issue` - Key of the newly edited issue

### Reads fields from config file at $HOME/jira/config.yml
- `issue`
- `project`
- `issuetype`
- `summary`
- `description`

### Writes fields to config file at $HOME/jira/config.yml
- `issue` - a key of an edited issue

### Writes fields to CLI config file at $HOME/.jira.d/config.yml
- `issue` - a key of an edited issue
