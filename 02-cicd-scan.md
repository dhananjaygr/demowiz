<div style="margin-right: 50px; margin-left: 30px;">

# Task: CI/CD Code Scanning
---

In this task, we will simulate part of a CI/CD pipeline where developers commit code to a GitHub repository. The Wiz GitHub Connector is able to scan for IaC misconfigurations, Vulnerabilities, and Secrets in committed codes.

## Commit misconfigured code and secret to repository

1. In your newly create GitHub repository, click on **Add file > Create new file**

1. Copy the contents from the block below and paste in the new file. Name it `Dockerfile`

1. Click on **Commit changes...**

1. In the *Proposed changes* pop-up select **Create a new branch..** and give it a name `task1`. 

1. Click on **Propose changes**

1. Add a new file to the same branch by select **< > Code**, then changing the branch to `task1`.

1. Once in the `task1` branch, click on **Add file > Create new file**.

1. Copy the contents from the block below and paste in the new file. Name it `awssecret.json`

1. Click on **Commit changes...**.

1. In the *Proposed changes* pop-up select **Commit directly to the *task1* branch**. Click on **Commit changes**.

1. Now lets create a Pull Request (PR), to move our new files into the `main` branch, which is in our case the production branch. You can click on the **Compare & pull request** button or go to the **Pull requests** menu and create a new PR, both will lead to the same *Open a pull request* workflow.

1. On the *Open a pull request* page, click on **Create pull request**.

1. In the Pull request commit conversation page, you will see the Wiz checks in action, and as result you should see the `Wiz IaC Scanner` and `Wiz Secret Scanner` failed.

1. Before addressing the issues found by the scans, lets look into what Wiz collects and shows in the portal.

## Analyze scan result in Wiz

1. In the Wiz portal, navigate to **Reports > Version Control Scans**.

1. Find your triggered scan. On the `Repository` column, look for your <github_user>/<repo_name>. Or you can use the *Repository* filter.

1. Open the details of your scan, lets look into some of the details.

    - **Event Properties** shows basic details of the scan, including the overall severity and trigger type (Pull Request or Scheduled)
    - **CI/CD Scan** shows the scan result and the number of findings per severity.
    - **Properties** shows scan duration and time, and most importantly what scan policies are enabled at the connector level.

1. Now lets look at the details of the **Pull Request Properties** section:

    This section shows who committed the code (author), the branch name (task), the base and committed (head) hashes, number of commits in the PR, number of files added, and the PR url.

1. The **Contains Configuration Findings** and **Secret Instances** sections show the IaC misconfiguration and secret findings respectively. 


## Address code commit issues

1. Back at your Github's PR page, within the check step, find the `Wiz IaC Scanner` line and click on **Details**.

1. Here you will see the High severity finding within the `Dockerfile` file. 

    `The 'Dockerfile' should contain the 'USER' instruction`

1. Find the link to `Wiz Secret Scanner` and click on it.

1. Here you will see the Secret finding, where we committed an AWS Access/Secret Key pair within our code.

In a production scenario, you would not want to add Access/Secret Keys inside your code. This is extremely dangerous, and can lead to compromise and priviledge escalation. There are alternatives like using an AWS role attached to the instances running the containers/application. 
As part of this lab, we will fix the Dockerfile problem, but leave the secret. We want to show that it's possible to bypass the PR checks (although not recommended)

1. From the PR's Checks page, navigate to **< > Code**.

1. Change your branch to `task1`.

1. Open the `Dockerfile`.

1. 

investigating in Wiz


addrssing problem

rerun check

create custom secret policy

rerun check

create vuln file

create PR

investigating in Wiz

Graph Query


</div>