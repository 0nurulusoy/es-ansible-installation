# ElasticSearch Instalation with Ansible

This is an Ansible playbook that installs and configures Elasticsearch on a server. The tasks performed by this playbook are:

- Update the server and install apt-transport-https package.
- Update package cache and fix missing dependencies by installing openjdk-11-jdk package.
- Set JAVA_HOME environment variable.
- Reload environment variables.
- Verify JAVA_HOME environment variable.
- Add Elasticsearch GPG key.
- Add Elasticsearch repository.
- Install Elasticsearch 8 on Ubuntu 20.04 LTS.
- Start Elasticsearch service.
- Check Elasticsearch service status.

In summary, this playbook installs and sets up Elasticsearch on a server by updating the server, installing required packages, and configuring the necessary environment variables and services.


Run this command manually,

echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list



### Before running the below commands, establish the SSH connection from ansible-node to es-nodes.

## Test the connect with below command

	ansible all -i inventory.ini -m ping

## Clone this repo to ansible-node

	git clone https://github.com/tryingtobecoder58/es-ansible-installation

## Run the Ansible-Playbook
	
	ansible-playbook -i inventory.ini playbook.yml
