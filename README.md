# Create a JIRA epic with tasks/subtaks

A script that builds JIRA tasks using postman collections and Newman. Updated: September 16, 2019

<img src="https://i.imgur.com/z0s4jc8.jpg" display="inline-block" width="310px" height="auto">

## Installation

1. Clone the repository.
    In Git Extension: Click Start, and select Clone repository...	 
	
    In Git Bash:

    ```bash
    c/git
    $ git clone https://github.com/JuliaBeingessner/JIRA-postman
    ```

1. Install `npm` (if you don't already have it).

    [Download](https://www.npmjs.com/get-npm)
    
    When setting up the installer, make sure that npm/node are added to your PATH.
    
1. Restart Git Bash.

1. Install dependencies.

    Go to the root folder:
	
	```cd C:/Git/JIRA-postman) ``` 
	
	Run the following command to install the dependencies:

    ```bash
    c/git/JIRA-postman
    $ npm install
    ```

### Folder structure

You should ignore most of what's in here. Click on one of the batch files to run the script.

<img src="https://i.imgur.com/ZtYP9ah.png">

- Reports are saved to `newman`. You can delete these files if not needed. The script will create a new folder if not there.

## Note about passwords

When you run the batch file, you are prompted to enter your OKTA `password` and `username`. Your credentials are stored in the local copy of the `MS_env.json` file. Git ignores changes to this file, but you should still be careful with which files you share. If after you run the script and you have uncommitted changes, it's going to be this file: `MS_env.json`.

Before you run the script to build JIRA tasks for the first time, run this:

```bash
git update-index --assume-unchanged source/globals/MS_env.json
```

This should remove this specific file from the git index, so even when the file changes, git won't ask you to push.

## Usage

To run the script, double-click the batch file:

1. `NP_checks` for NPrinting.

1. `Sense_checks` for Sense.

1. `QV_checks` for QlikView.

The batch file opens a cmd shell. Enter the details as prompted.

- trigram = your Qlik trigram

- password = JIRA password (usually the same as your Qlik login password)

- JIRA label = HLP_QualityCheck

- epic title = product MS Checks

- epic desc = This is the description field in the JIRA task.

- due date = Can be any date. It is added before the description of each task.

### The report

After the program runs, you'll get a confirmation message and a status report opens in your browser.

<img src="https://i.imgur.com/a2mGUj5.png">

Click the first green bar at the top of the page to expand it. In the reponse body you'll see the epic JIRA number. All JIRA tasks are nested under that. If there are errors, the bar(s) appear red. Expand the bar to see the error code and use Google to search for JIRA error code values.

Reports are saved to the `Newman` folder. The newman folder is in the gitignore file so new reports won't be added to github.

### Errors

|Status code|Problem|Solution|
|:---:|---|---|
|201|Good API request|n/a|
|401|Unauthorized|Try the script again. Make sure to use your trigram `ABC` or `abc` and the password that you use to log into JIRA `password123`.|
|403|Forbidden|Unable to create tasks. Not necessarily an authentication issue, but the script can't access the JIRA API. Try clearing the browser cache, logging in/out of JIRA, and restarting your machine. Ask someone else to try running the script, if they succeed then it is probably solvable by restarting your computer.|

### Changing the script text
If you want to change the wording in the auto-generated tasks: don't. Ping Julia. 

<img src="https://i.imgur.com/wK84XJB.jpg">