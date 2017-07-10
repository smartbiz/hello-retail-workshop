# Installing AWS CLI

If not already installed, we have provided a script in the workshop project root:

```sh
 sudo ./setup-aws-cli.sh
```

Otherwise, please follow the [guidance from AWS to install the CLI](http://docs.aws.amazon.com/cli/latest/userguide/installing.html).

### Ubuntu 16.04 LTS

```sh
 python --version
 // python3 --version
```

```
 sudo curl -O https://bootstrap.pypa.io/get-pip.py
 python get-pip.py --user
 // Find your shell's profile script in your user folder
 ls -a ~
 // Add an export command to profile script.
 export PATH=~/.local/bin:$PATH
 // Load the profile into your current session.
 source ~/.profile
 // Verify that pip is installed correctly.
 pip --version
```

```
 // Use pip to install the AWS CLI.
 pip install awscli --upgrade --user
 // aws --version
 // pip install awscli --upgrade --user
```

## Configuring Credentials

- You must have permissions to perform these required IAM actions.

> `AWS Console` > `IAM` > `Users` - `serverless_admin` with "Access type" = `Programmatic access`

```
 // Refer to the downloaded file `credentials.csv`
 Access key ID:
 Secret access key:
```

- The AWS CLI may be used to configure the user's credentials stored in the `~/.aws/credentials` file, using the following command:

```
 aws configure
```

When prompted, enter your AWS `Access Key ID` and your `Secret Access Key` then your optional default region (`ap-southeast-2`: Sydney) and output format. Once done, that information should persisted under
 the default profile and will be used for all AWS-CLI or Serverless.com commands.

## Select Credentials Profile to Use

Serverless and the AWS CLI can share the credentials stored in `~/.aws/credentials` file.
 Use the `AWS_PROFILE` environment variable to select the profile to use when calling the AWS managed services.

```
export AWS_PROFILE=<profile name from credentials file>
```

*NOTE: The profile named `[default]` in your credentials file will be used if `AWS_PROFILE` is not set.*