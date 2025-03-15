![github-header-image (1)](https://github.com/user-attachments/assets/fb42157b-093a-420d-8b69-372b0c74496f)

&nbsp;

&nbsp;

&nbsp;

&nbsp;




### **Prerequisites**

### **1. Sign up for a free account and subcription with Rapid API to get an API key.**

  - **Go to [Rapid API](https://rapidapi.com/)  website and register, confirm registartion.**

    
![image](https://github.com/user-attachments/assets/f4668245-4e26-4fcd-95ea-54c4ca264601)


  - Enter information, then click "Sign Up"

![image](https://github.com/user-attachments/assets/58d22ef7-bec5-4eb2-bebe-6c9076a10fb7)


  - Enter verification code sent to your email.

![image](https://github.com/user-attachments/assets/85d3dc48-0a1a-4ade-8329-784dc35eec9c)


  - Fillout the survey about yourself.

![image](https://github.com/user-attachments/assets/c9e059f5-4152-40b4-8d6c-f077b0401bf1)


  - Go to any free Sports API, "I used NCAA". Click "see all" in the search bar to view all the options.

![image](https://github.com/user-attachments/assets/f2d946b1-390d-43f4-9065-1834994a1798)

![image](https://github.com/user-attachments/assets/6a8becfd-c375-47a3-92e1-1636700ec1fc)

![image](https://github.com/user-attachments/assets/90da1d05-9755-42c5-b865-f44f977a7a16)


  - Click on the blue "Subscribe to Test" on the top right, validate that you aren't being charged, enter your payment information, then Click "Subscribe".

![image](https://github.com/user-attachments/assets/84136326-4c0b-4cc6-a4dd-7232447530a7)

![image](https://github.com/user-attachments/assets/b3d4add2-36d9-447d-95da-cfa087aecf74)

![image](https://github.com/user-attachments/assets/87862a21-46c8-45fa-922d-42d62cefb150)


  - Test your API to verify functionality by clicking the blue icon "Test Endpoint" before using any API. You will see green check displaying positive validation.

![image](https://github.com/user-attachments/assets/be695242-6229-4435-a4e2-b7980e98635d)

- Copy your API Key to use later.



## **2** Verify prerequites are installed 

  - Docker should be pre-installed in most regions.
  - Verify installation with this command:

```bash
docker --version
```

  - AWS CloudShell has AWS CLI pre-installed.
  - Verify installation with this command:

```bash
aws --version
```
  - Python3 should be pre-installed.
  - Verify installation with this command:

```bash
python3 --version
```

## **3** Retrieve AWS Account ID

Copy your AWS Account ID Once logged in to the AWS Management Console Click on your account name in the top right corner You will see your account ID Copy and save this somewhere safe because you will need to update codes in the labs later

![image](https://github.com/user-attachments/assets/08d2bf57-859a-47f0-91c2-1cd5284b97dc)



## **4** Retrieve Access Keys and Secret Access Keys
  
  - You can check to see if you have an access key in "Security Credentials"
 
  - Scroll down until you see the "Access Keys" section.
  
  - You will not be able to retrieve your secret access key so if you don't have that saved somewhere already, you need to create an access key. If you have two already, deactivate and delete one under "Actions" to create another. 

![image](https://github.com/user-attachments/assets/fa9746a6-88cb-4a6a-a7c1-2fb52700074e)


## **4. Create an S3 Bucket if you don't already have one.** 

# START HERE - Local

## **Step 1: Clone The Repo and go to the "SRC" directory**

```bash
git clone https://github.com/MJaloui/NCAAGameHighlights.git
cd src
```

![image](https://github.com/user-attachments/assets/ab8d22e7-81b8-481b-8a9e-51178730da69)


## **Step 2: Add API Key to AWS Secrets Manager** 

- There are two options to do this. You can do this in the AWS CLI or manually store it in AWS.

- Option 1, Store API key with AWS CLI:

- Copy and Paste command, Swap in the sports API and Secret Access key. Remove the curly bracket "{}".

  - Enter cmd:
    
```bash
aws secretsmanager create-secret \
    --name my-api-key \
    --description "API key for accessing the Sport Highlights API" \
    --secret-string '{"api_key":"YOUR_Secret_Access_Key"}' \
    --region us-east-1
```
 
    - Option two, store API key manually in AWS:
  
  - Go to "Secrets Manager" and click "Store a new secret."

![image](https://github.com/user-attachments/assets/68b6e4e3-e2c3-4edd-9ba3-5c6573991692)

![image](https://github.com/user-attachments/assets/e8aca805-12f0-4be2-a237-840c721032de)


  - Choose secret type, enter your key, and click "Next".

![image](https://github.com/user-attachments/assets/2a3fd1f3-501e-46f8-ba11-1e826e1335cd)

![image](https://github.com/user-attachments/assets/35203063-72ef-4a93-8a7b-0f087d84130a)
  

  - Enter secret name "my-api-key" and an optional description, then click "Next". Scroll down and click "Next" again.


![image](https://github.com/user-attachments/assets/421c1e37-4a7e-40e4-bb0f-73446c28226b)

![image](https://github.com/user-attachments/assets/72909eeb-c6f9-4476-a96b-47d2eed617c4)

![image](https://github.com/user-attachments/assets/6130f5e1-332d-401b-9a94-39f73aee75b1)


  - Click "Store".

![image](https://github.com/user-attachments/assets/a6b07666-5cf9-44dd-9970-dc28814a295c)


- You will see a green "Successful" banner displayed.
- If you click the the refresh icon on the top right, the stored API key will appear.
  
![image](https://github.com/user-attachments/assets/d4f637d9-6489-4954-8d5c-3ac7970cb5f0)









## **Step 3: Create an IAM role or user**

  - In the search bar type "IAM" or access IAM from the Console home.

 ![image](https://github.com/user-attachments/assets/b0701adc-cda6-48c6-94d4-3651ac6a95fb)


  - Click Roles -> Create Role

![image](https://github.com/user-attachments/assets/cd365c9b-c91e-498d-92aa-75757d8dd4cc)

![image](https://github.com/user-attachments/assets/3c3e7a99-091e-4cc2-bc2a-108d9d1a0770)



  - For the Trusted entity type "AWS service, enter the Use Case service "S3" and click "Next"

![image](https://github.com/user-attachments/assets/c9492454-33e7-41e1-8192-f04e597f846c)

![image](https://github.com/user-attachments/assets/95678b10-7743-4c67-8255-2f520214de52)


  - Under Add Permission search for AmazonS3FullAccess, MediaConvertFullAccess and AmazonEC2ContainerRegistryFullAccess, and then click next.

![image](https://github.com/user-attachments/assets/7b46fc9f-080f-41e0-87ae-a7b6d04be0ec)

![image](https://github.com/user-attachments/assets/0f85f544-25a8-49dd-a9c4-6d55bbca2f17)
 
![image](https://github.com/user-attachments/assets/8248fe4a-a40a-4777-9f5e-857d4fc0997e)

![image](https://github.com/user-attachments/assets/bb170fa9-4378-4dc7-83e5-f327d10c85e3)



Under Role Details, enter "HighlightProcessorRole" as the name, and enter a "Description" (optional). 

![image](https://github.com/user-attachments/assets/a2208f67-d9b6-41d4-b357-f12827dfaf11)



Edit the Trust Policy.

  - Click "Edit", select trusted entity type "Custom trust policy", Paste the custom JSON script to replace the displayed JSON script, then click "Next".

![image](https://github.com/user-attachments/assets/d478bdb9-da53-44ce-b4d6-164ad91611be)

![image](https://github.com/user-attachments/assets/40768e3b-32d0-467f-af24-de1aae1edbfd)



  - Copy and paste the custom Trust Policy to replace the current JSON script, add ID and username in the script(remove the quotaions """ and angle brackets "<>"):

```bash
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": [
          "ec2.amazonaws.com",
          "ecs-tasks.amazonaws.com",
          "mediaconvert.amazonaws.com"
        ],
        "AWS": "arn:aws:iam::<"your-account-id">:user/<"your-iam-user">"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

![image](https://github.com/user-attachments/assets/bbf058a9-0a4f-4f8c-8198-2dd3c65e1694)

  - Click "Next", then "Create role". A green banner will appear if all configurations are successful.

 ![image](https://github.com/user-attachments/assets/7fbfe831-024d-4081-a787-a8de5fb645aa)

![image](https://github.com/user-attachments/assets/d3c433a7-a231-419a-9e90-262a170d2af8)

![image](https://github.com/user-attachments/assets/f6aad639-9a45-4c2f-9069-76dfa768f0b4)

 
## **Step 4: Update .env file**

  - Enter this command and copy the output for mediaconvert endpoints, number 7 below.

```bash
aws mediaconvert describe-endpoints
```

![image](https://github.com/user-attachments/assets/938a2ffd-a1b8-4f52-b2c0-45d7de5744e2)

  - Edit .env file with the command below.
    
```bash
nano .env
```

1. API_URL=https://sport-highlights-api.p.rapidapi.com/basketball/highlights
2. RAPIDAPI_HOST=sport-highlights-api.p.rapidapi.com
3. RAPIDAPI_KEY=your_rapidapi_key_here
4. AWS_ACCESS_KEY_ID=your_aws_access_key_id_here
5. AWS_SECRET_ACCESS_KEY=your_aws_secret_access_key_here
6. S3_BUCKET_NAME=your_S3_bucket_name_here
7. MEDIACONVERT_ENDPOINT=https://your_mediaconvert_endpoint_here.amazonaws.com
8. MEDIACONVERT_ROLE_ARN=arn:aws:iam::your_account_id:role/YourMediaConvertRole

![image](https://github.com/user-attachments/assets/fdd89b8f-47f5-4f2f-8b51-5c3c8aea9862)




## **Step 5: Secure .env file with read and write permissons to the owner**

```bash
chmod 600 .env
```

![image](https://github.com/user-attachments/assets/569aaf36-32e2-412b-b99c-636ae89e2a66)


## **Step 6: Locally Build & Run The Docker Container**

Run:

```bash
docker build -t highlight-processor .
```

![image](https://github.com/user-attachments/assets/a837e41b-cd61-46a5-b7cc-617d38e5ba8f)


Run the Docker Container Locally:

```bash
docker run --env-file .env highlight-processor
```

![image](https://github.com/user-attachments/assets/810dd3ec-d2d4-4ff9-b8be-7be5123fcc5d)

![image](https://github.com/user-attachments/assets/d5d3c568-7783-44e7-8b50-fdbea591eced)

![image](https://github.com/user-attachments/assets/160f897b-5599-40c9-b324-0347379da41b)


     
  - **This will run fetch.py, process_one_video.py and mediaconvert_process.py and the following files should be saved in your S3 bucket:**

    - Optional - Confirm there is a video uploaded to s3://<your-bucket-name>/videos/first_video.mp4

![image](https://github.com/user-attachments/assets/9f90a33d-3580-44db-bc50-a2440d9af873)

![image](https://github.com/user-attachments/assets/900b1c65-efea-4526-946a-3fec137325e1)

![image](https://github.com/user-attachments/assets/a893ea1e-9786-46c6-bb89-dd160b35e864)

![image](https://github.com/user-attachments/assets/5dcbc5b0-6946-4652-a090-b4ee736df16f)

![image](https://github.com/user-attachments/assets/f3a92813-d3b1-4d78-98ad-c95b3c857a79)

![image](https://github.com/user-attachments/assets/95418d5f-1066-4186-a957-3302da507a45)
 
  
  
  
  
  - **Optional - Confirm there is a JSON file filled with highlight links, uploaded to s3://<your-bucket-name>/highlights/baseketball_highlights.json. Go back to objects.**

![image](https://github.com/user-attachments/assets/6f551f84-9197-49ca-bb96-96a3000fc5b5)

![image](https://github.com/user-attachments/assets/57624785-1378-4efc-be22-adeba516f572)

![image](https://github.com/user-attachments/assets/12bda6ab-cc3e-4055-8b7f-2d289bf3636d)

![image](https://github.com/user-attachments/assets/8a48144d-82ef-4831-9366-25b006f61aa2)



---



# Part 2 - Terraform Addition

### **Setup terraform.tfvars File**



1. In the github MJaloui, repo "NCAAGameHighlights.md", there is a resources folder. Copy the entire contents.

![image](https://github.com/user-attachments/assets/5a2444bf-e81b-4b1a-aa79-5f9b1bb8f3bd)


2. In the AWS Cloudshell or vs code terminal, in the "terraform" directory, create the file vpc_setup.sh and paste the script inside. Save and exit out of the file.

```bash
nano vpc_setup.sh
```

![image](https://github.com/user-attachments/assets/73fb2f4b-6a98-41d1-b2f5-2d166a09731f)

![image](https://github.com/user-attachments/assets/1d6b9e0d-a92e-4658-a4e1-ccb7126b8fbd)


3. Run the script to recieve variables.

```bash
bash vpc_setup.sh
```
![image](https://github.com/user-attachments/assets/7d222421-627f-4988-9d32-5944866e7916)



4. You will see variables in the output, paste these variables into lines 8-13 in the "terraform.tfvars" file. Add the AWS ID for "raidapi_ssm_parameter_arn", add the "mediaconvert_endpoint" as well (you will run the command on step 6 to recieve endpoint).

 ![image](https://github.com/user-attachments/assets/cd2331ee-b6c0-4635-9281-4c13d4b4c835)
  



5. Store your API key in AWS Secrets Manager, run the command below in the CLI.

```bash
aws ssm put-parameter \
  --name "/YOUR_PROJECT/RAPIDAPI_KEY" \
  --value "YOUR_SECRET_KEY" \
  --type SecureString
```

![image](https://github.com/user-attachments/assets/80029afb-20e8-4628-a92c-51d34f7e3ad7)



6.  Run the following script to obtain your mediaconvert_endpoint (copy and paste output in "terraform.tfvars" script, save, and exit).

```bash
aws mediaconvert describe-endpoints
```

![image](https://github.com/user-attachments/assets/87f57f5b-c3d1-46bb-98f0-9a59b8e6daaa)



7. Leave the mediaconvert_role_arn string empty



### **Run The Project**

1.  Navigate to the terraform directory in VS Code
From the src folder.

```bash
cd terraform
```

2. **Initialize terraform working directory**

```bash
terraform init
```

![image](https://github.com/user-attachments/assets/e9752534-39a0-42fe-ba49-c94867e0ede0)



**3. Check syntax and validity of your Terraform configuration files**

```bash
terraform validate
```

![image](https://github.com/user-attachments/assets/c7bd8d4e-ea00-45f2-9fef-2be440646c28)



**4. Display execution plan for the terraform configuration**

     - **Enter the value "dev" after you run the plan command.**

```bash
terraform plan
```

![image](https://github.com/user-attachments/assets/8871489c-28c5-485e-8199-e8a68ade4a85)




**5. Apply changes to the desired state**

```bash
terraform apply -var-file="terraform.dev.tfvars"
```

  - **Enter the value "dev", then "yes" for approval, after running the "apply" command.**

![image](https://github.com/user-attachments/assets/a6885852-c886-4849-a400-dd859c2fc047)

![image](https://github.com/user-attachments/assets/c19d94a7-181b-4961-8892-b3958871c3e0)



**6. Build the docker image for AWS deployment - ensure you are at the "src" folder before running commands** 

```bash
docker build -t highlight-pipeline:latest .
docker tag highlight-pipeline:latest <AWS_ACCOUNT_ID>.dkr.ecr.<REGION>.amazonaws.com/highlight-pipeline:latest
```

![image](https://github.com/user-attachments/assets/749d90f2-92df-45a0-a81c-b9b5d5630838)

![image](https://github.com/user-attachments/assets/a1832c12-92ae-4bda-b0b4-959a0e5dbfbd)



7.Log into ECR & Push (add AWS ID)

```bash
aws ecr get-login-password --region us-east-1 | \
  docker login --username AWS --password-stdin <YOUR_AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com

docker push <AWS_ACCOUNT_ID>.dkr.ecr.<REGION>.amazonaws.com/highlight-pipeline:latest
```

![image](https://github.com/user-attachments/assets/63f4de28-cbed-49cb-8eaa-298050fb2779)

![image](https://github.com/user-attachments/assets/53b42286-d979-4ac2-956b-523fbae7e5bb)




























