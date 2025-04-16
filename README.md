# NCAA Game Highlights


![image](https://github.com/user-attachments/assets/cd0982fe-f3e9-4150-9245-64a3394fa239)

---

## 🔷 Project Highlights 🔷

🏀 This project pulls NCAA basketball game highlights using the RapidAPI and processes them in a fully containerized environment.  
📦 It uses Docker for packaging and deployment, making it easy to run anywhere, and Terraform to automatically set up AWS infrastructure like S3 buckets, IAM roles, and ECS.  
🎞️ Game highlight videos are stored and managed in AWS S3, then converted using AWS MediaConvert with custom video and audio settings.  
🧩 The Python script `run_all.py` runs the scripts in chronological order and provides buffer time for the tasks to be created.  
🔐 Environment variables are securely stored in a `.env` file, keeping sensitive information out of the source code and making the setup more secure and portable across environments.  
☁️ It showcases how to combine API integration, cloud automation, containerization, and video processing in a streamlined pipeline.

---

## 🔧 Capabilities 🔧

🔹 Fetches NCAA basketball game highlights using RapidAPI  
🔹 Automatically stores raw JSON data and video files in AWS S3  
🔹 Converts and optimizes video files using AWS MediaConvert  
🔹 Orchestrates the entire workflow with a single Python script (`run_all.py`)  
🔹 Uses `.env` file for secure and flexible configuration management  
🔹 Deploys infrastructure with Terraform for repeatable, scalable environments  
🔹 Runs inside a Docker container for easy portability and setup  

---

## 🚨 Technologies 🚨

🔹 **Cloud Provider**: AWS  
🔹 **Core Services**: S3, MediaConvert, IAM  
🔹 **External API**: RapidAPI (NCAA Game Highlights API)  
🔹 **Programming Language**: Python 3.x  
🔹 **Version Control**: Git  
🔹 **Environment Management**: .env file for secure variable handling  
🔹 **Containerization**: Docker  
🔹 **Infrastructure as Code**: Terraform  
🔹 **Orchestration**: Python script (`run_all.py`) for process sequencing  
🔹 **Security**: IAM roles and policies for controlled access to AWS services  

---

## 👀 Instructions 👀

### 🔹 Prerequisites 🔹

1. Create a RapidAPI Account at [RapidAPI.com](https://rapidapi.com)  
2. Verify Tools Are Installed: Docker, AWS CLI, Python3  
3. Retrieve AWS Account ID  
4. Retrieve AWS Access & Secret Keys  

---

### **Steps:** ➡️❗ [Click Here To View Detailed Visual Steps](https://github.com/MJaloui/NCAAGameHighlights.md/blob/main/VisualStepsHere.md) ❗⬅️

1. **Clone the Repo**  
   ```bash
   git clone https://github.com/MJaloui/weather---dashboard
   ```

2. **Add API Key to AWS Secrets Manager**

3. **Create IAM Role or User**  
   - Add permissions: `AmazonS3FullAccess`, `MediaConvertFullAccess`

4. **Update .env File**

5. **Secure the .env File**  
   ```bash
   chmod 600 .env
   ```

6. **Build & Run Docker Container Locally**  
   ```bash
   docker build -t highlight-processor .
   docker run --env-file .env highlight-processor
   ```

   ✅ This will run `fetch.py`, `process_one_video.py`, and `mediaconvert_process.py`.

7. **Optional – Confirm there is a video uploaded to:**  
   - `s3:///<your-bucket-name>/videos/first_video.mp4`  
   - `s3:///<your-bucket-name>/processed_videos/`  

---

## ✅ What We Learned

1. Working with Docker and AWS Services  
2. Identity Access Management (IAM) and least privilege  
3. How to enhance media quality  

---

## 🌱 Future Enhancements

1. Using Terraform to enhance the Infrastructure as Code (IaC)  
2. Increasing the amount of videos processed and converted with AWS MediaConvert  
3. Change the date from static (specific point in time) to dynamic (e.g., now, last 30 days)  

---

## 🚀 Part 2 - Terraform Bonus

### Setup `terraform.tfvars` File

1. Copy contents from the `Resources` folder in the GitHub repo  
2. In AWS CloudShell or VS Code terminal, create the file `vpc_setup.sh` and paste the script inside  
3. Run the script and paste these variables into the `terraform.tfvars` file  
4. Store your API key in AWS Secrets Manager  
5. Run AWS script to obtain your `mediaconvert_endpoint`  
6. Leave the `mediaconvert_role_arn` string empty  

---

### Run The Project

1. Navigate to the terraform folder/workspace in VS Code  
2. Initialize terraform working directory  
3. Check syntax and validity of your Terraform configuration files  
4. Display execution plan for the terraform configuration  
5. Apply changes to the desired state  
6. Build the Docker image for AWS deployment (ensure you're in the `src` folder)  
7. Log into ECR & Push  
8. Destroy ECS and ECR resources using script in resource folder  
9. Confirm Video Files were created  

---

## ✅ What We Learned

1. Deploying local Docker images to ECR  
2. A high-level overview of Terraform files  
3. Networking - VPCs, Internet Gateways, private and public subnets  
4. SSM for saving secrets and pulling into Terraform  

---

## 🌱 Future Enhancements

1. Automating the creation of VPCs/networking infra, media endpoint  
