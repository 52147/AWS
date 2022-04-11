# Building Modern Java Applications on AWS

## SDK:
- stand for software development kit
- also know as a devkit
- SDK is a set of software-building tools for spefic platform
- including the building block
- debuggers and, a framwork or code libraiies.
  
  - java SDK:
  - Maven (a java SDK)
    - Maven manages dependencies and built.
    - Maven usea a file called the project object moddel(POM), to build the project alongside a set of plut0ins.
    - The POM file is written in XML.
    - create your POM, define dependencies and build lifecycle, and then your project will be built to those specs.
    - You must include the AWS SDK in the POM of Mavan project in order to use it.   
  
  - Gridle:
    -  use a build doc Gradle file that allows you to define your build tasks and your dependencies. 
 
## API:
- application programming interface
- api faciliates communication between 2 platforms,
  it does this by allowing its proprietary software to be leveraged by third party developers. 

API vs. SDK
- do not need to choose betwen API and SDK
- an SDK often contains a least one API

- API serve to define how different platforms work together
- faciliate interation via specifications(protocols)
- serve as one of tools in a complete kit.

- SDK are the complete kit
- They go beyond faciliation to provide everything for building new software for a specific platform or programming language.


## Credential:

- a subject may own security related attrubutes, whuich are referred to as credentials.
- credential may contain information used to authenticate the subject to new services.
- include passwords, Kerberos tickets, and public key certificates.

  - AWS credential chain:
    - that looks for credentials in this order:
       Environment variables - AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY.
    - For local development, use credential and config files for access key, rigion, and profile configuration.
    
    - defaultClient():
    - AWSSimpleSystemManagementClientBuilder.defaulatClient()
    - AmazonS3ClientBuilder.defaultClient()
    - we are calling this default client method on each builder.
    - This method create a service client with the default configuration, using what is called the default provider chain to load credentials and other configuration like what AWS region are trying to submit your API call to.
    
    - The default credential chain, checks a few different places for your AWS credentials.
    - First, it checks the environment variables.
    - If it can't find the credentials or region, it then checks the Java system properties.
    - After that, it checks the default credential profile.
    - If there was not a file configured, then it checks to see if you are running indife of a container using Amazon Elastic Container Service or ECS.
    - If so, it will use the credential supplied by ECS.
    - Finally, if it can't find credential in any of those places, it will check the instance profile crentials.

    - essentially seeing if there is a role associated with the instance that the code is running on, like an EC2 instance, 
      for example. If the credentials or the region can't be determined from the environment that the application is running in, 
      the call to the default client will fail and the client will not be instantiated. 
    - You need those credentials somewhere in order for this to work. In this case, we're developing on a Cloud nine instance, so credentials are coming from the managed credentials supplied by Cloud9,

    develop locally:
    - If you were developing locally, you would want to make sure that your configuration and credentials files were configured with your region, AWS Access Key ID and AWS Secret Access Key. 
    - Then in your code, you can use methods on the builder to set the region where your credentials are coming from
    
    - no hard code credential:
    - One thing to note though, is you don't want to hard code your credentials in your code. 
    - If you hard code your credentials in your code, and then you upload them to say, GitHub, well, now your credentials are on the internet. 
    - You really want to rely on role-based access when possible, or if you're using Cloud9, using the Manager Credentials as fine as well. 
    - If you're using local development on your local machine, then using a credentials file is okay. But we recommend that you use role-based access as much as possible and avoid hard coding your credentials inside of your code. Once you have your client for whatever AWS service you are trying to work with. You can then call the methods on that client and interact with the AWS API. 


## AWS Cloud9:

- AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you to write, run, and debug code from any machine with just a browser.

## Amazon S3:
- is object storage built to strore and retrieve amount of data from anywhere.

 - S3 bucket:
   - is a public cloud storage resource available in Amazon Web Services(AWS) simple storage services.
   - an object storage offering
   - are similar to file folders, store objects, which are consists of data and its descriptive metadata.

 - S3 select(AWS API):
   - read drag data from an S3 bucket
   - allows you to read a subset of data out of an S3 object using sequel queries.
   - being able to query a subset of your data from an S3 object is actually really powerful.
   - S3 charges you based on the number of requests, the amount of data, and the amoount of data being transferred.
   
   - oftentimes, when you work with large datasets, you might download the entire object from s3
     and then go through it line by line searching for relevant data.
   - This is both cheaper and faster than downloading the entire object, when you may only need a subset.
   - All of the processing is on the S3 side, not on the application side.
   - So you don't have to code for that filtering through an entire object.
  
   - S3 select only supports certain types of data to be queried, and in our situation, the JSON data isn't JSON, which S3 slect does support.

AWS systems manager(SSM):

- formerly known as Amazon Simple Systems Manager(SSM) and Amazon EC2 Systems Manager(SSM).
- is an AWS service that you can use to view and control your infrastructure on AWS.
- Using the System Manager console, you can view operational data from multiple AWS services and automate operational tasks accross your AWS resources.
- Systems Manager helps you maintain security and compliance by scanning your managed nodes and reporing on(or taking corrective action on) any police violations it detects.



  
## AWS system manager parameter store(AWS API):
- paremeter store lets you store user-defined key-value pairs.
- we are going to use this service to store our S3 bucket name, 
  whether Dragon data is located, and the filename or what we call the key.
- This way, if the bucket or the filename ever changes, we won't need to go back in and change the code.
- Instead, the paremeter can be updated in parameter store.
- Then the code will always pull the latest information every time it is run.


servive client object:
- To make a request to Amazon Web Services, you first create service client objects fot this specific AWS service you are trying to interact with.
- The recommended way to do this is to use the Service Client Builder.


## AWS exception:

- Notice how there weren't any try catch blocks or throw statements for AWS specific exceptions. 
- That is because the AWS SDK for Java uses unchecked exceptions. 
- There are two main categories of exceptions to be aware of. 
  1. AmazonServiceException :
     - First, you have the AmazonServiceException or one of its subclasses. This is the most common exception that you'll experience when using the AWS SDK for Java. 
     - This exception represents an error response from an AWS service. For example, if you try to read data from an S3 bucket that doesn't exist, you would receive an Amazon S3 exception, which is a subclass of the AmazonServiceException class. The second category of exceptions are AmazonClientExceptions. 
  2. AmazonClientException :
     - An AmazonClientException indicates that a problem occurred inside the Java client code, either while trying to send a request to AWS or while trying to parse a response from AWS. 
     - For example, if your code tries to make an API call but has no access to the Internet, you would get this type of exception. 



## AWS serverless application model(SAM):
- The AWS Serverless Application Model, or SAM, is an open-source framework for building serverless applications. 
- It provides shorthand syntax to express functions, APIs, databases and more, giving you the ability to define an application you want to model using a few short lines per resource. 
- During deployment, SAM transforms and expands the SAM syntax into AWS cloud formation syntax, enabling you to build serverless applications faster. 
- A serverless application in this case is a combination of AWS Lambda functions, event resources, and other resources that work together to perform your distributed tasks. 
- SAM consists of two main components, 
  -  AWS SAM template specification and AWS SAM command line interface. 
    1. The SAM template specification:  
       - is used to define the serverless application. 
       - It provides you with the syntax to describe everything that makes up your serverless application. 
    2. The SAM command line interface, or SAM CLIL : 
       - is the tool used to build the applications that are defined by the SAM templates. 
       - This provides the commands that enable you to verify that template files are written according to specification, work with resources, package and deploy the application to the AWS Cloud, and so on. 
       - Keep in mind that this is a different CLI from the traditionally used AWS CLI, as this is specifically used with SAM.



 - SAM is an extension of CloudFormation. 
   - Because of that, you get the same deployment capabilities. 
   - You can define resources, use your CloudFormation in your SAM template. 
   - And you can use the full suite of resources, intrinsic functions, and other template features that are available in CloudFormation. 
   - Because SAM integrates with other AWS services, there are a lot of benefits that are provided. 
     - For one, SAM makes it easier to organize related components and resources and operate on a single stack. 
     - You can use it to share configurations between resources and deploy related resources together as a single-versioned entity. 
     - Also, because SAM enables you to templatize what you're deploying, it makes it possible for you to use and enforce best practices, such as code reviews. 
     - And because this is a template, you are able to test and deploy the same environment without as much worry about unintended changes.

- SAM can build severless application:
- Additionally, you can use SAM with a suite of AWS tools for building serverless applications. 
- You can discover new applications in the AWS serverless application repository. 
- You can use the AWS Cloud9 IDE to author, test, and debug your SAM-based serverless applications. 
- You can build a deployment pipeline for your serverless applications using AWS CodeBuild, AWS CodeDeploy, and AWS CodePipeline. 
- And you can even use AWS CodeStar to build out project structure, code repository, and a CI/CD pipeline that's automatically configured for you


## AWS lambda:
- AWS Lambda is a serverless compute service that runs your code in response to events and automatically manages the underlying compute resources for you. 
- These events may include changes in state or an update, such as a user placing an item in a shopping cart on an ecommerce website.
