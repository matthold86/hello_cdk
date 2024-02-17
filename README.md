
# Create AWS S3 Bucket Using AWS CDK

## Summary

This project provides the basic structure for deploying an AWS S3 bucket using the AWS CDK toolkit with python.


## Replicate the Work

Initialize the app by using the cdk init command. Specify the app template and your preferred programming language with the --language option.

```
$cdk init app --language python
```

After the app has been created, enter the following command to activate the app's Python virtual environment on a Windows operating system.

```
$ .venv\Scripts\activate
```

Once the virtualenv is activated, we can install the required dependencies.

```
$ pip install -r requirements.txt
```

At this point, the CDK app contains a single stack. Next, we will define an Amazon Simple Storage Service (Amazon S3) bucket resource within the stack. To do this, we will import and use the Bucket L2 construct from the AWS Construct Library. It's important to add a few S3 bucket properties like versioning and encryption. The screenshot below shows the CDK Stack intialization code that adds `versioned=True` and `S3 Managed Encryption`. When deploying the cdk stack, we'll need appropriate AWS credentials configured locally to successfully deploy.

![image](https://github.com/matthold86/hello_cdk/assets/114833075/497a2547-4ff0-4df7-9f08-f5cd8779ca70)


We can now synthesize the CloudFormation template for this code.

```
$ cdk synth
```


Once the CloudFormation template is created, deploy the stack with the default AWS credentials on your local environment. I created a new user with proper access credentials for this project before deploying. Once the new User was configured locally, deployment was easy! 

```
$ cdk deploy
```

Below is a screenshot of the S3 bucket created from this cdk stack deployment.

![image](https://github.com/matthold86/hello_cdk/assets/114833075/ef03ff61-f15e-43dd-a8d4-0f9ce927e673)

## AWS CodeWhisperer

AWS CodeWhisperer is a valuable tool especially for deploying cdk stacks. The LLM was trained code internal to Amazon so the suggestions for writing code compatible with AWS Services is usually helpful and accurate. One particularly helpful area is navigating the IAM Users and Roles. Provided a general description of what the User needs to be able to accomplish on AWS, CodeWhisperer will respond with the appropriate permission policies required for the User. This expedited deployment while ensuring AWS security best practices.


