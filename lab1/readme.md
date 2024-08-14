# Command Line Interface (Part I)

## Goal
Install / confirm the command line interface (CLI) and log into the TAS test account at Wells Fargo.

Approximate time: 30 minutes

## Exercise:
### Install the CLI
Check to see if you have a CLI already installed. Open a terminal/command window and type `cf --version`. If you see that you have an installed version greater than 6, you can skip the install.

Visit `https://console.run.pivotal.io/tools`. Download and run the installer for your platform.

Verify your install by opening a terminal/command window and typing `cf --version`. You now have a Cloud Foundry client that can communicate with any Cloud Foundry installation.


### Explore cf help
1. Type `cf help`. Scroll through the list of commands available to the CLI. Notice that they are organized by category. You will become familiar with most of the categories in this course.
2. Type `cf help login`. Use this approach whenever you need a refresher on any of the CLI commands. Because login has an alias, you could have also have typed `cf help l`.

### Log into App Manager (TAS from a browser)
In a browser, navigate to The Wells Endpoint - this will be provided on a whiteboard. This is Pivotal's hosted Cloud Foundry installation. If you already have an account, log in, otherwise create a free account.

In Web UI, click on the Tools tab to see the connection information for the CLI. You will use this information to login to the CLI (in fact, you can copy and paste from this window).

### Log into Web UI with the CLI
Use the CLI's `cf login` command to log in to your account (you may have to logout first). You can use the information from the browser window to help you, and you can use `cf help login`.

In the Web UI, click on the Tools tab to see the connection information for the CLI. You will use this information to login to the CLI (in fact, you can copy and paste from this window).

Once you have logged in, type `cf target` to view you current API endpoint, User, Org and Space.

### View the .cf directory
On your local machine's file system, navigate to you home directory and find the .cf directory. It may be hidden depending on your settings.

Open the config.json file and notice that your connection settings are cached in that file.

### If you have time

Browse the commands in cf help and see what you discover :)

