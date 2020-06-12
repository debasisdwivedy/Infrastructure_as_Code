## Install pre-requisite packages (RHEL 7.4)
sudo rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm  
sudo yum update  
sudo yum check-update; sudo yum install -y gcc libffi-devel python-devel openssl-devel sshpass  
sudo yum install -y python-pip python-wheel  

## Install Ansible and Azure SDKs via pip
sudo pip install ansible[azure]  

## Install azure cli
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc  

sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'  

sudo yum install azure-cli  

## Create service principal
az login  
az ad sp create-for-rbac --query '{"client_id": appId, "secret": password, "tenant": tenant}'

## Update service principal in variable file (group_vars)  
subscriptionID:  
clientID:  
clientSecret:  
tenantID:  

## Modify variables if required in variable file (group_vars) 

## Run the playbook  
ansible-playbook site.yaml  

