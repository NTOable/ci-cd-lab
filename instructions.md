Lab Assignment: Continuous Integration & Branch Protection ("Break the Build")
Estimated Duration: 45–60 minutes

Format: Individual Hands-On Activity

Tech Requirements: Git, Node.js installed locally, a free GitHub account

Lab Purpose

In professional software development, code is never pushed directly to production without automated checks.

In this lab, you will build an automated Continuous Integration (CI) pipeline using GitHub Actions, establish branch protection rules, and practice resolving automated build failures before merging code into main.

Task Breakdown
Phase 1: Local Setup
Create a local folder named ci-cd-lab.

Initialize a Node.js project (npm init -y) and install Jest as a development dependency (npm install --save-dev jest).

Update your package.json to include "test": "jest" under scripts.

Create calculator.js with basic math operations (add and subtract).

Create calculator.test.js to write unit tests for those operations using Jest.

Verify your setup locally by executing npm test in your terminal. Ensure all tests pass.

Phase 2: Configure the CI Workflow
Create the directory path .github/workflows/.

Inside that directory, create a pipeline configuration file named ci.yml.

<-------------- CONTINUE HERE ---------------->

Configure the workflow to trigger on push and pull_request events targeting the main branch.

Define a job that spins up an ubuntu-latest container, sets up Node.js 20, installs project dependencies via npm ci, and runs npm test.

Create a new GitHub repository named ci-cd-lab, push your code to main, and verify that the workflow runs successfully under the Actions tab on GitHub.

Phase 3: Enforce Branch Rules
Navigate to your repository's Settings -> Branches.

Add a Branch Protection Rule for the main branch.

Check the following options:

Require a pull request before merging

Require status checks to pass before merging (select your build-and-test pipeline check).

Phase 4: The "Break and Fix" Challenge
Create and switch to a feature branch: git checkout -b feature/calculator-updates.

Break the Build: Modify calculator.js so that the add function returns incorrect logic (e.g., returning a - b instead of a + b).

Commit and push your branch to GitHub.

Open a Pull Request (PR) targeting main. Observe how GitHub Actions runs automatically and blocks the merge button due to failing unit tests.

Fix the Build: Revert the logic error on your local feature branch, commit, and push the change.

Confirm that the status check turns Green / Passed and unblocks the PR merge button. Merge your PR into main.

Deliverables & Submission
Submit the following via the LMS portal:

Repository Link: A direct link to your merged Pull Request demonstrating the passing status check.

Reflection Response (2–3 sentences): Why is running unit tests inside an isolated CI container (like an Ubuntu runner) more reliable than trusting a teammate who says "it worked on my machine"?