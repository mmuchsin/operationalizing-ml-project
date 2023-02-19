# Operationalizing an AWS ML Project

The goal of this project will be to use several important tools and features of AWS to adjust improve, configure, and prepare a machine learning model for production-grade deployment.

## Training and Deployment on Sagemaker
### Initial Setup
1. Create and open a sagemaker notebook instance
2. Install unzip command
   ```
   sudo yum install unzip -y
   ```

![notebook](src/img/1-notebook-instance-crop.png)
I choose `ml.t3.medium` as the cheapest compute instance just for running the jupyter notebook

### Download and Upload Data to an S3 Bucket
```
wget -nc https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip
unzip -q dogImages.zip
aws s3 cp ./dogImages s3://operationalizing-ml/dataset
```
take a screenshot showing that you've set up an S3 bucket. Include this screenshot in your final submission.
![s3_bucket](src/img/2-s3-setup-crop.png)

#### Training and Deployment
#### Single Instance
I tried to use a spot instance for this single instance training. And the cheapest
spot instance available in this account is `ml.c5.2xlarge` 
because ml.g4dn.xlarge spot instance is not available in the provided account.
cpu optimized instance ml.c5.2xlarge spot instance $0.0751/h normal price $0.204/h


#### Multi Instance
#### Endpoint

## EC2 Training
### EC2 Setup
Think about what type of instance you want to create, based on cost, computing power, and launch speed. Decide the type of instance you want, create it in your workspace, and write a justification of why you chose the instance type you did.

Note: when you select an AMI for your EC2 instance, you should select the "Amazon Deep Learning AMI" so that you can use its libraries.
![ec2_setup](src/img/4.1-ec2-c5l-instance-setup-crop.png)

### Preparing for EC2 model training
After your code is finished running, you can open the TrainedModels directory on your EC2 instance and take a screenshot of the model that has been saved in it, to provide evidence that you completed this step.

### Training and saving on EC2
![ec2_training](src/img/4.2-ec2-c5l-instance-train-crop.png)
## Sagemaker Training vs EC2 Training
sagemaker:
- invoke training job
- input data from s3
- model data to s3
- price?
- scalability?
- easy setup

ec2:
- training on local instance
- load data from local instance directory
- save model data to local directory
- 

### Lambda Function Setup
You should also notice the content of this Lambda function. You may have to set up many Lambda functions in your career, so do your best to understand how this one is set up so you can follow its example. In particular, you should notice how it invokes the endpoint (with the invoke_endpoint() method) and how it sets up the return statement. Write at least 1 paragraph describing how this function is written and how it works.
![lambda_ok](src/img/5-lambda-crop.png)

### Security and Testing
Write about the security of your AWS workspace in your writeup. Are there any security vulnerabilities that need to be addressed? Think about some common security vulnerabilities. For example, roles that have "FullAccess" policies attached may be too permissive and may lead to problems. Roles that are old or inactive may lead to vulnerabilities because they may belong to people who are no longer working on the project and who may not be careful about ensuring the project's success. You might also find roles for functions that the project is no longer using, which should probably be deleted.
![iam_role](src/img/6-lambda-role-crop.png)

### Concurrency and Auto-scaling
When you set up concurrency and auto-scaling, you will make several choices about configuration. Write about the choices you made in the setup of concurrency and auto-scaling, and why you made each of those choices.

>You will submit screenshots for Sagemaker instance setup, EC2 setup, Lambda function setup, and IAM security.You will submit screenshots for Sagemaker instance setup, EC2 setup, Lambda function setup, and IAM security.You will submit screenshots for Sagemaker instance setup, EC2 setup, Lambda function setup, and IAM security.