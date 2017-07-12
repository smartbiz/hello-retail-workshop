# Lesson 0: Before the workshop
Goal: Install everything needed for the workshop and confirm that you can login to a public cloud v2 account.

We advise using the native command line tools for your OS.

### Step 1: Clone the Serverless-Retail-Workshop repo on your local machine

Install git on your local machine by following instructions here: https://git-scm.com/downloads

### Windows

> Make sure the folder path to git is added to the `PATH` environment variable so that you can run the following commands from the windows command line.

> If it is not then you can add it by clicking `Windows` Key --> search `System` --> click `Advanced system settings` --> select `Advanced` tab --> click `Environment Variables` --> Under `System variables` select `PATH`/`Path` --> click `Edit` --> at the end of the `Variable value` add `;<path-to-git\cmd-folder-on-your-local-machine>` (example, `;C:\Program Files\Git\cmd`). **Make sure you add semi-colon before the path**

Go to https://github.com/smartbiz/serverless-retail-workshop and clone it locally:

```sh
 git clone https://github.com/smartbiz/serverless-retail-workshop.git
```

If you would like to provide fixes or changes to the workshop, please [fork the repository](https://help.github.com/articles/fork-a-repo/) and submit a [pull request](https://help.github.com/articles/creating-a-pull-request-from-a-fork/).

### Step 2: Install node.js and run script

Ensure that you have [Node.js](https://nodejs.org/en/) (v4.3 or later) installed.

If you do not already have NodeJs installed, we suggest using [NVM](https://github.com/creationix/nvm#installation) to allow side-by-side install of different node versions.  If you would prefer to install a specific version globally, please download the latest LTS version for your operating system from https://nodejs.org/en/download/.

After successfully installing NodeJs, please run the following script provided at the root directory of this repository in order to check your NodeJS version and install dependencies for your lesson projects.

#### OS X

```sh
 cd <path-to-local-workshop-dir>
./setup-nodejs.sh
```

#### Ubuntu 16.04 LTS

```sh
 cd <path-to-local-workshop-dir>
 sudo ./setup-nodejs.sh
```

#### Windows
 
```bat
 cd <path-to-local-workshop-dir>
 setup-win.bat
```

### Step 3: Setup your AWS credentials

Install the [AWS-CLI](SETUP-AWS-CLI.md) and use the `aws configure` command to setup your credentials.

Your credentials are located in the AWS Console under:

IAM --> users --> select your user ID --> security credentials tab

If you use any AWS profile other than the default, you'll need to provide that profile name to the environment via the `AWS_PROFILE` variable:

#### OS X
```sh
 export AWS_PROFILE=<your-profile>
```

#### Windows
```bat
 set AWS_PROFILE=<your-profile>
```

### Step 4: install serverless node package on your machine.

Install the serverless.com deployment framework - this will make it easy to deploy serverless components to AWS.

#### OS X or Windows
```sh
 sudo npm install -g serverless
 // npm install -g serverless@1.11.0
```

If you are on OS X and have used sudo to install libraries (and are thereby hitting permissions issues running the above, execute the following: 
`sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}`
