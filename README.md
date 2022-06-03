# Projects Registry automation
## Important links
* Form to add new projects - https://airtable.com/shrPNzCqzHNpaXadS
* Heroku project https://dashboard.heroku.com/apps/projects-registry
* Projects registry in AirTable - [Link for Editors](https://airtable.com/invite/l?inviteId=invWhcDFV3eyOUTb3&inviteToken=1ab8c186b3f16aa0bf3df07ba33a1dd9542f337c6c3b64a3ffe8a76bc1af3516&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts) & [Admins](https://airtable.com/invite/l?inviteId=invrPMrnLZXeFFy7d&inviteToken=b54114962ba59f6ee259717471493380842a58e4f4622477fb44723270680ed2&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts)


## Requirements
1. AirTable table with Form
2. Heroku account with access to project
3. Git on local computer
4. Jira Software space with tempalte projects. **NB** Only issue tree is copied to new projects
5. GitHub account for repos
6. Python knowledge + libraries listed in _requirements.txt_ and _runtime.txt_ in repo
 

## Updating code
Simple way is
1. Only once - Install Heroku Cli (instructions for Win/Mac [here](https://devcenter.heroku.com/articles/heroku-cli))
2. Once in a while - do `heroku login`, continue in browser
3. do `heroku git:clone -a projects-registry`
4. enter folder by `cd projects-registry`

When done editing, `git add`, then `git commit`, then `git push heroku`, app will be deployed, rebuilt and launched


## Updating Config Variables
Config variables are managed in [project settings](https://dashboard.heroku.com/apps/projects-registry/settings) on Heroku, click [Reveal Config Vars].

**NB** After editing any of the variables, container will restart taking the changes into account, last codebase will be used.

* AIRTABLE_BASE:  App Id, go to AirTable Help -> API, select desired database and ID will be shown
* AIRTABLE_KEY: Generate API key [here](https://airtable.com/account)
* AIRTABLE_TABLE: Same as App (Base) Id above, just with Table
* CC_TEMPL: Chose cookiecutter template for repos, currently [Data Science](https://github.com/drivendata/cookiecutter-data-science)
* GIT_TOKEN: Github token generated [here](https://github.com/settings/tokens), requires `repo` permissions
* GIT_U: GitHub username
* JIRA_EMAIL: Self-explanatory, account requires `admin` permissions for space
* JIRA_SRV: Self-explanatory, https://rob-sandberg.atlassian.net
* JIRA_TEMPL: possible values are listed in [Jira API docs](https://developer.atlassian.com/cloud/jira/platform/rest/v2/api-group-projects/#api-rest-api-2-project-post)
* JIRA_TOKEN: Generate in [account settings -> security](https://id.atlassian.com/manage-profile/security)
* LOGGING: TRACE (detailed) or DEBUG (medium) or INFO (superficial)
* SACRED: List of templates-projects' keys, currently only MIG for Migration project, separated by semicolon
* TZ: e.g. America/Denver, internal instance timezone. Heroku logs are always UTC

