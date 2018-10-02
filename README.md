# Create JIRA epic with tasks/subtaks

A script to build JIRA tasks using postman collections and Newman.

<img src="source/images/postman.png" display="inline-block" width="100px" height="auto">
<img src="source/images/jira.png" display="inline-block" width="100px" height="auto">

## Note about passwords

When you run the batch file, you are prompted to enter `pw` and `un`. Your credentials are stored in the local copy of the `MS_env.json` file. Git ignores changes to this file, but you should still be careful with which files you share.

## Installation

1. Clone the repository.

    ```bash
    c/git
    $ git clone https://github.com/kyleweishaar/JIRA-postman
    ```

1. Install `npm` (if you don't already have it).

    Download [here](https://www.npmjs.com/get-npm).
    
    When setting up the installer, make sure that npm/node are added to your PATH.
    
1. Restart Git Bash.

1. Install dependencies.

    From the root folder (c/git/JIRA-postman), run the following command to install the dependencies:

    ```bash
    c/git/JIRA-postman
    $ npm install
    ```

### Folder structure

You can ignore most of what's in here. Click on one of the batch files to run the script.

![folder](source/images/folders.png)

- Reports are saved to `newman`. You can delete these files if not needed. The script will create a new folder if not there.

## Usage

To run the script, double-click the batch file:

1. `NP_checks` for NPrinting.

1. `Sense_checks` for Sense.

1. `QV_checks` for QlikView.

The batch file opens a cmd shell. Enter the details as prompted.

- trigram = Qlik trigram

- password = JIRA/Qlik password

- JIRA label = product_MS_Checks

- epic title = product MS Checks

- epic desc = This is the description field in the JIRA task.

- due date = Can be any date. It is added before the description of each task.

### The report

After the program runs, you'll get a confirmation message and a status report opens in your browser.

![report](source/images/report.png)

Click the first green bar at the top of the page to expand it. In the reponse body you'll see the epic JIRA number. All JIRA tasks are nested under that. If there are errors, the bar(s) appear red. Expand the bar to see the error code and use Google to search for JIRA error code values.

Reports are saved to the `Newman` folder. The newman folder is in the gitignore file so new reports won't be added to github.
