
### 1. **Introduction to DevOps and Python**
#### Description:
This module introduces the fundamental concepts of DevOps and how Python can be used for automation.

#### Example Code:
```python
# Setting up a virtual environment for Python development
import os
import subprocess

# Create a virtual environment
subprocess.run(['python3', '-m', 'venv', 'devops_env'])

# Activate the virtual environment
activate_script = os.path.join('devops_env', 'bin', 'activate')
subprocess.run(['source', activate_script], shell=True)

print("Development environment setup complete!")
```

### 2. **Version Control with Git**
#### Description:
Learn to automate Git tasks such as committing, pushing changes, and creating branches using Python.

#### Example Code:
```python
import subprocess

def git_command(command):
    result = subprocess.run(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
    if result.returncode != 0:
        print(f"Error: {result.stderr}")
    else:
        print(result.stdout)

# Example usage: Automate git add, commit, and push
git_command(['git', 'add', '.'])
git_command(['git', 'commit', '-m', 'Automated commit message'])
git_command(['git', 'push', 'origin', 'main'])
```

### 3. **Continuous Integration (CI)**
#### Description:
Set up Jenkins to automate build and test processes.

#### Example Code:
```python
import requests

# Trigger a Jenkins job using Python
jenkins_url = 'http://localhost:8080/job/your_job/build'
response = requests.post(jenkins_url, auth=('your_username', 'your_password'))

if response.status_code == 201:
    print("Build triggered successfully!")
else:
    print(f"Failed to trigger build: {response.status_code}")
```

### 4. **Continuous Deployment (CD)**
#### Description:
Automate deployments using AWS CodeDeploy or Azure Pipelines with Python.

#### Example Code (AWS CodeDeploy):
```python
import boto3

client = boto3.client('codedeploy', region_name='us-west-2')

response = client.create_deployment(
    applicationName='MyApp',
    deploymentGroupName='MyDeploymentGroup',
    revision={
        'revisionType': 'S3',
        's3Location': {
            'bucket': 'my-bucket',
            'key': 'my-app.zip',
            'bundleType': 'zip'
        }
    }
)

print(f"Deployment ID: {response['deploymentId']}")
```

### 5. **Infrastructure as Code (IaC)**
#### Description:
Use Terraform with Python to provision and manage infrastructure.

#### Example Code:
```python
import subprocess

# Initialize Terraform
subprocess.run(['terraform', 'init'])

# Apply Terraform configuration
subprocess.run(['terraform', 'apply', '-auto-approve'])

print("Infrastructure provisioning complete!")
```

### 6. **Configuration Management**
#### Description:
Automate server configuration and management using Ansible.

#### Example Code:
```python
import subprocess

# Run an Ansible playbook
subprocess.run(['ansible-playbook', 'my_playbook.yml'])

print("Server configuration complete!")
```

### 7. **Containerization and Orchestration**
#### Description:
Automate Docker and Kubernetes tasks using Python.

#### Example Code (Docker):
```python
import docker

client = docker.from_env()

# Build and run a Docker container
client.images.build(path='.', tag='my_app')
client.containers.run('my_app', detach=True)

print("Container is running!")
```

### 8. **Monitoring and Logging**
#### Description:
Set up monitoring and logging using Prometheus and Grafana.

#### Example Code:
```python
import requests

# Configure Prometheus with Python
prometheus_url = 'http://localhost:9090/api/v1/status/config'
response = requests.get(prometheus_url)

if response.status_code == 200:
    print("Prometheus configuration:")
    print(response.json())
else:
    print(f"Failed to fetch configuration: {response.status_code}")
```

### 9. **Security Automation**
#### Description:
Automate security scans and integrate them into CI/CD pipelines.

#### Example Code:
```python
import subprocess

# Run a security scan using a tool like Bandit
subprocess.run(['bandit', '-r', 'your_project'])

print("Security scan complete!")
```

### 10. **Backup and Recovery Automation**
#### Description:
Automate backup processes for databases and application data.

#### Example Code:
```python
import subprocess

# Backup a MySQL database
subprocess.run(['mysqldump', '-u', 'user', '-p', 'database_name', '>', 'backup.sql'])

print("Database backup complete!")
```

### 11. **Networking Automation**
#### Description:
Automate network configuration and management tasks.

#### Example Code:
```python
import boto3

client = boto3.client('route53')

# Create a new DNS record
response = client.change_resource_record_sets(
    HostedZoneId='Z3M3LMPEXAMPLE',
    ChangeBatch={
        'Changes': [
            {
                'Action': 'CREATE',
                'ResourceRecordSet': {
                    'Name': 'example.com',
                    'Type': 'A',
                    'TTL': 300,
                    'ResourceRecords': [{'Value': '192.0.2.1'}]
                }
            }
        ]
    }
)

print(f"DNS record created: {response}")
```

### 12. **Final Project: End-to-End DevOps Pipeline**
#### Description:
Build a fully automated CI/CD pipeline integrating all the components learned in the course.

#### Example Code:
```python
import subprocess
import boto3
import docker

# Step 1: Automate Git tasks
def git_automation():
    subprocess.run(['git', 'add', '.'])
    subprocess.run(['git', 'commit', '-m', 'Automated commit'])
    subprocess.run(['git', 'push', 'origin', 'main'])

# Step 2: Trigger Jenkins build
def trigger_jenkins_build():
    jenkins_url = 'http://localhost:8080/job/your_job/build'
    response = requests.post(jenkins_url, auth=('your_username', 'your_password'))
    if response.status_code == 201:
        print("Build triggered successfully!")

# Step 3: Deploy with AWS CodeDeploy
def deploy_with_codedeploy():
    client = boto3.client('codedeploy', region_name='us-west-2')
    response = client.create_deployment(
        applicationName='MyApp',
        deploymentGroupName='MyDeploymentGroup',
        revision={
            'revisionType': 'S3',
            's3Location': {
                'bucket': 'my-bucket',
                'key': 'my-app.zip',
                'bundleType': 'zip'
            }
        }
    )
    print(f"Deployment ID: {response['deploymentId']}")

# Step 4: Provision infrastructure with Terraform
def provision_infrastructure():
    subprocess.run(['terraform', 'init'])
    subprocess.run(['terraform', 'apply', '-auto-approve'])

# Step 5: Configure servers with Ansible
def configure_servers():
    subprocess.run(['ansible-playbook', 'my_playbook.yml'])

# Step 6: Manage Docker containers
def manage_docker():
    client = docker.from_env()
    client.images.build(path='.', tag='my_app')
    client.containers.run('my_app', detach=True)

# Step 7: Set up monitoring with Prometheus
def setup_monitoring():
    prometheus_url = 'http://localhost:9090/api/v1/status/config'
    response = requests.get(prometheus_url)
    if response.status_code == 200:
        print("Prometheus configuration:")
        print(response.json())

# Step 8: Run security scans
def run_security_scans():
    subprocess.run(['bandit', '-r', 'your_project'])

# Step 9: Automate database backups
def backup_database():
    subprocess.run(['mysqldump', '-u', 'user', '-p', 'database_name', '>', 'backup.sql'])

# Step 10: Configure DNS with Route53
def configure_dns():
    client = boto3.client('route53')
    response = client.change_resource_record_sets(
        HostedZoneId='Z3M3LMPEXAMPLE',
        ChangeBatch={
            'Changes': [
                {
                    'Action': 'CREATE',
                    'ResourceRecordSet': {
                        'Name': 'example.com',
                        'Type': 'A',
                        'TTL': 300,
                        'ResourceRecords': [{'Value': '192.0.2.1'}]
                    }
                }
            ]
        }
    )
    print(f"DNS record created: {response}")

# Execute the pipeline
if __name__ == '__main__':
    git_automation()
    trigger_jenkins_build()
    deploy_with_codedeploy()
    provision_infrastructure()
    configure_servers()
    manage_docker()
    setup_monitoring()
    run_security_scans()
    backup_database()
    configure_dns()

    print("End-to-End DevOps pipeline executed successfully!")
```

This comprehensive guide and example scripts cover various DevOps automation tasks using Python. You can build on these examples to create more complex workflows and tailor them to your specific needs. Feel free to ask if you need further elaboration on any particular module or task!
