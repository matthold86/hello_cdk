
# Create AWS S3 Bucket Using AWS CDK

## Summary

This project provides the basic structure for deploying an AWS S3 bucket using the AWS CDK toolkit with python.


## Replicate the Work

The `cdk.json` file tells the CDK Toolkit how to execute your app.

This project is set up like a standard Python project.  The initialization
process also creates a virtualenv within this project, stored under the `.venv`
directory.  To create the virtualenv it assumes that there is a `python3`
(or `python` for Windows) executable in your path with access to the `venv`
package. If for any reason the automatic creation of the virtualenv fails,
you can create the virtualenv manually.

To manually create a virtualenv on MacOS and Linux:

```
$ python -m venv .venv
```

After the init process completes and the virtualenv is created, you can use the following
step to activate your virtualenv.

```
$ source .venv/bin/activate
```

If you are a Windows platform, you would activate the virtualenv like this:

```
% .venv\Scripts\activate.bat
```

Once the virtualenv is activated, we can install the required dependencies.

```
$ pip install -r requirements.txt
```

It's important to add a few S3 bucket properties like versioning and encryption. The screenshot below shows the modified initialization code that adds `versioned=True` and `S3 Managed Encryption`. When deploying the cdk stack, we'll need appropriate AWS credentials configured locally to successfully deploy.

![image](https://github.com/matthold86/hello_cdk/assets/114833075/497a2547-4ff0-4df7-9f08-f5cd8779ca70)

At this point we can now synthesize the CloudFormation template for this code.

```
$ cdk synth
```


Once the CloudFormation template is created, you can deploy the stack with the default AWS credentials on your local environment. I created a new user with proper access credentials for this project before deploying. Once the new User was configured locally, deployment was easy! 

```
$ cdk deploy
```

Below is a screenshot of the S3 bucket created from this cdk stack deployment.

![image](https://github.com/matthold86/hello_cdk/assets/114833075/ef03ff61-f15e-43dd-a8d4-0f9ce927e673)

## AWS CodeWhisperer

AWS CodeWhisperer is a valuable tool especially for deploying cdk stacks. The LLM was trained code internal to Amazon so the suggestions for writing code compatible with AWS Services is usually helpful and accurate. One particularly helpful area is navigating the IAM Users and Roles. Provided a general description of what the User needs to be able to accomplish on AWS, CodeWhisperer will respond with the appropriate permission policies required for the User. This expedited deployment while ensuring AWS security best practices.


