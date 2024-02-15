# Flutter Web Application Dev Container

This repo sets up a containerized development environment that supports the development of Flutter web applications.

## Requirments
* Docker is installed and running
* VSCode is installed with the following extensions:
  * Remote Development Extension Pack

## Creating DevContainer
1. Clone this repo to a destination of your choosing.  

2. Open the cloned repo folder in VSCODE.  

3. If the correct extensions are installed and Docker is running, a notification should appear to "Reopen in Container," click this. Else, open the small blue remote connection window in the bottom left and select the same thing ("Reopen in Container").  

Once the Dev Container fully opens, you are good to go for development.

## Creating and Running Flutter Applications
To create a flutter app, enter the following command in the devcontainer's terminal:
* flutter create {app name of your choosing}  

Now, to run your app, cd into the newly created app directory and enter the following command:
* flutter run -d web-server
