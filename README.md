# ElasticSearch Instalation with Ansible

This Ansible playbook sets up a multi-node Elasticsearch. The playbook assumes Ubuntu 20.04 LTS as the operating system.

## As long as you don't specify the version this playbook will install latest version of 8.x.x of Elasticserach.

You can try to install a specif version, by changing to older repository url on the playbook.

## Requirements
- Ansible 2.10 or higher
- Access to three Ubuntu 20.04 LTS servers
- SSH access to each server with sudo privileges

### Usage

1. Clone this repository to your local machine:

		git clone https://github.com/tryingtobecoder58/es-ansible-installation

2. Modify the inventory.ini file to include the hostnames or IP addresses of your three servers.

3. Modify the elasticsearch.yml file to set the cluster name, JVM heap size, network host, and xpack security settings as desired.

4. Run the Ansible-Playbook, be sure your user have permission to make changes on the remote hosts, or you can add -u root, parameter to auth as a root user to other hosts
	
		ansible-playbook -i inventory.ini playbook.yml


### Configuration

The variables can be set in the elasticsearch.yml.j2 file to customize the Elasticsearch installation.


- Check the cluster health with below command.
		
		curl -XGET http://es02:9200/_cluster/health?pretty=true
		curl -XGET http://es02:9200/_cat/nodes?pretty=true


- The output should look like this for 3 node cluster, which has 2 datanodes.
		https://i.ibb.co/pvSfpJT/Screenshot-at-Mar-01-18-29-12.png



To uninstall

	sudo apt-get --purge autoremove elasticsearch -y
	sudo apt-get remove --purge elasticsearch 
	sudo rm -rf /etc/elasticsearch
	sudo rm -rf /var/lib/elasticsearch
