# CodePush Tutorial By Nam
## Description
A quick CodePush tutorial by me

Note that **`<appName>`** in this document is the name when you create the app on CodePush not your app name on Visual Studio Code

For more details:
  + Server: [Click here](./api/README.md)
  + CLI: [Click here](./cli/README.md)
## Requirements
+ Lastest NodeJS version
+ A github's account
## Install CLI
1. Clone project to anywhere on you computer
2. Open cmd and locate to [CLI folder](./cli)
3. Install dependencies by running `npm install`
4. Build the CLI by running `npm run build`
5. Install CLI globally to run CodePush by cmd or any console by running `npm install -g`
6. You're ready to use CodePush
## Basic commands
### Authentication
CodePush use github's oauth2 as authentication
+ If this is your first time or your new github's account:
1. Open cmd
2. Register using `code-push-standalone register`
3. A page will popup, click **`GitHub`** on the website to get Access Key
4. Copy the access key and pass it in cmd
5. Press enter
6. You're are now logged in
+ If you already registered than just login:
1. Open cmd
2. Login using `code-push-standalone login`
3. A page will popup, click **`GitHub`** on the website to get Access Key
4. Copy the access key and pass it in cmd
5. Press enter
6. You're are now logged in

To logout, simply run `code-push-standalone logout`
### Create new app
To create new app, make sure to login as **`gesodev@gmail.com`**. Ask a Lai for password.
**`Steps`**:
1. Open cmd
2. Create new app with `code-push-standalone app add <appName>`
3. Remember to copy deployment keys and paste it in [here](https://gist.github.com/gesodev/4277d18c3dc12997dd4535c6d6f7f169)

When you create an app, the app is only visible to **`gesodev@gmail.com`** cause this account is the owner of this app\
To make it visible to others github's accounts, you need to add these accounts collaborator:
**`Steps`**:
1. Open cmd
2. Add collaborator by running `code-push-standalone collaborator add <appName> <registeredEmail>`
3. Check if the collaborator was added by running `code-push-standalone collaborator ls <appName>`

For example: `code-push-standalone collaborator add NTF-IOS gesodev@gmail.com`

#### App configuration
##### Android
Path: `<projectSource> > android > app > src > main > res > values > string.xml`\
Add these lines to file:
```shell
<string moduleConfig="true" name="CodePushServerUrl">http://1.53.252.173:5931</string>
<string moduleConfig="true" name="CodePushDeploymentKey"><appKey></string>
```
##### IOS
Path: `<projectSource> > ios > <appPackageName> > Info.plist`\
Add these lines to file:
```shell
<key>CodePushServerURL</key>
<string>http://1.53.252.173:5931</string>
<key>CodePushDeploymentKey</key>
<string><appKey></string>
```
## Deploy an app
Just run this command
```shell
code-push-standalone release-react <appName> <platform> --mandatory --rollout 100 --deploymentName Staging --targetBinaryVersion <versionNumber>
```
+ **`appName`**: your code push app name
+ **`platform`**: android || ios
+ **`versionNumber`**: your app version number
