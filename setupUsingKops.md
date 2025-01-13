
# Kubernetes-Zero-to-Hero

Welcome to the **Kubernetes-Zero-to-Hero** repository! This project aims to make Kubernetes accessible and straightforward for beginners. We'll guide you through the installation and setup of Kubernetes using KOPS on AWS EC2 instances. This repository is a work in progress, continuously updated to provide comprehensive guidance on Kubernetes management and deployment.

## Kubernetes Installation Using KOPS on EC2

### Step 1: Set Up Your Environment

You can either launch an EC2 instance on AWS or use your personal laptop for this setup. Ensure the following dependencies are installed:

1. **Python 3** - Essential for running AWS CLI and other scripts.
2. **AWS CLI** - Required to interact with AWS services.
3. **kubectl** - Kubernetes command-line tool for controlling Kubernetes clusters.

### Step 2: Install Dependencies

To install the necessary tools, follow these commands:

1. **Add Kubernetes APT repository key:**

   ```bash
   curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   ```

2. **Add Kubernetes repository to your APT sources list:**

   ```bash
   echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

3. **Update your package list and install required packages:**

   ```bash
   sudo apt-get update
   sudo apt-get install -y python3-pip apt-transport-https kubectl
   ```

4. **Install AWS CLI using pip:**

   ```bash
   pip3 install awscli --upgrade
   ```

5. **Add AWS CLI to your system PATH:**

   ```bash
   export PATH="$PATH:/home/ubuntu/.local/bin/"
   ```

### Step 3: Install KOPS

KOPS (Kubernetes Operations) simplifies the creation, configuration, and management of Kubernetes clusters on AWS. Install KOPS with the following steps:

1. **Download the latest release of KOPS:**

   ```bash
   curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
   ```

2. **Make the KOPS binary executable:**

   ```bash
   chmod +x kops-linux-amd64
   ```

3. **Move the KOPS binary to your local bin directory:**

   ```bash
   sudo mv kops-linux-amd64 /usr/local/bin/kops
   ```

### Step 4: Configure AWS Permissions

Ensure your IAM user has the necessary permissions. If you're using an admin user, these permissions are generally available by default. Assign the following permissions:

- **AmazonEC2FullAccess**
- **AmazonS3FullAccess**
- **IAMFullAccess**
- **AmazonVPCFullAccess**

### Step 5: Configure AWS CLI

Set up your AWS CLI by running the following command and entering your AWS credentials:

```bash
aws configure
```

### Step 6: Kubernetes Cluster Installation

Follow these steps carefully to install and configure your Kubernetes cluster.

#### 1. Create an S3 Bucket

KOPS uses S3 buckets to store the state of your cluster. Create an S3 bucket with the following command:

```bash
aws s3api create-bucket --bucket kops-vishal-storage --region us-east-1
```

#### 2. Create the Cluster

Use KOPS to create your Kubernetes cluster. The command below creates a cluster named `demok8scluster.k8s.local`:

```bash
kops create cluster --name=demok8scluster.k8s.local --state=s3://kops-vishal-storage --zones=us-east-1a --node-count=1 --node-size=t2.micro --master-size=t2.micro --master-volume-size=8 --node-volume-size=8
```

#### 3. Edit Cluster Configuration

KOPS generates a configuration file for the cluster, which may include resources beyond the free tier. Edit the configuration as needed:

```bash
kops edit cluster demok8scluster.k8s.local
```

#### 4. Build the Cluster

Update the cluster to apply your configuration changes:

```bash
kops update cluster demok8scluster.k8s.local --yes --state=s3://kops-vishal-storage
```

This process will take a few minutes. Once completed, verify the installation:

```bash
kops validate cluster demok8scluster.k8s.local
```

This command checks if the cluster is up and running. If successful, your Kubernetes cluster is ready to use!

## Conclusion

You've now set up a basic Kubernetes cluster using KOPS on AWS. Continue exploring Kubernetes to deploy applications, manage resources, and scale your services efficiently. This repository will be updated with more advanced topics and tutorials to help you become a Kubernetes expert!
