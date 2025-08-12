# Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS

## How to Run?

### **STEPS**

---

### **1. Clone the repository**
```bash
git clone https://github.com/stone-coding/Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS.git
cd Build-a-Complete-Medical-Chatbot-with-LLMs-LangChain-Pinecone-Flask-AWS
````

---

### **2. Create a conda environment**

```bash
conda create -n medibot python=3.10 -y
conda activate medibot
```

---

### **3. Install the requirements**

```bash
pip install -r requirements.txt
```

---

### **4. Create a `.env` file**

In the root directory, add your Pinecone & OpenAI credentials:

```
PINECONE_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

---

### **5. Store embeddings to Pinecone**

```bash
python store_index.py
```

---

### **6. Run the application**

```bash
python app.py
```

Then open:

```
http://localhost:5000
```

---

## Tech Stack Used

* Python
* LangChain
* Flask
* GPT
* Pinecone
* AWS (EC2, ECR)
* CI/CD Deployment with GitHub Actions

---

## AWS Deployment Steps

1. **Login to AWS console.**
2. **Create IAM user for deployment** (with specific access):

   * `AmazonEC2ContainerRegistryFullAccess`
   * `AmazonEC2FullAccess`
3. **Create ECR repo** to store/save docker image
   Save the URI:

   ```
   315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot
   ```
4. **Build docker image** of the source code.
5. **Push docker image to ECR**.
6. **Launch EC2 instance** (Ubuntu).
7. **Install Docker in EC2**:

   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
   ```
8. **Pull docker image from ECR** in EC2.
9. **Run docker image** in EC2.
10. **Configure EC2 as a self-hosted GitHub runner**:

    * Go to **Settings > Actions > Runners > New self-hosted runner**
    * Choose OS
    * Run the provided commands in EC2 terminal
11. **Setup GitHub Secrets**:

    * `AWS_ACCESS_KEY_ID`
    * `AWS_SECRET_ACCESS_KEY`
    * `AWS_DEFAULT_REGION`
    * `ECR_REPO`
    * `PINECONE_API_KEY`
    * `OPENAI_API_KEY`

```
