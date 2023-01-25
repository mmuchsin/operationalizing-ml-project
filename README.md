# Operationalizing an AWS ML Project

The goal of this project will be to use several important tools and features of AWS to adjust improve, configure, and prepare a machine learning model for production-grade deployment.

## Training and Deployment on Sagemaker
### Initial Setup
1. Create and open a sagemaker notebook instance
2. Install unzip command
   ```
   sudo yum install unzip -y
   ```
-take a scheenshot of your sagemaker instance setup
-write about sagemaker instance you created, including a justification of why you choose th instance type you did

ml.t3.medium as the cheapest just for running the jupyter notebook

### Download and Upload Data to an S3 Bucket
```
wget -nc https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip
unzip -q dogImages.zip
aws s2 cp ./dogImages s3://operationalizing-ml/dataset
```
take a screenshot showing that you've set up an S3 bucket. Include this screenshot in your final submission.

#### Training and Deployment
#### Single Instance
because ml.g4dn.xlarge spot instance is not available in the provided account.
cpu optimized instance ml.c5.2xlarge spot instance $0.0751/h normal price $0.204/h

#### Multi Instance
#### Endpoint

## EC2 Training
### EC2 Setup
Think about what type of instance you want to create, based on cost, computing power, and launch speed. Decide the type of instance you want, create it in your workspace, and write a justification of why you chose the instance type you did.

Note: when you select an AMI for your EC2 instance, you should select the "Amazon Deep Learning AMI" so that you can use its libraries.

### Preparing for EC2 model training
After your code is finished running, you can open the TrainedModels directory on your EC2 instance and take a screenshot of the model that has been saved in it, to provide evidence that you completed this step.

### Training and saving on EC2

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
