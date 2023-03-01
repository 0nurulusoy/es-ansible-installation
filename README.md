# ElasticSearch Instalation with Ansible

This Ansible playbook sets up a multi-node Elasticsearch cluster with two data nodes and one master/ingest node. The playbook assumes Ubuntu 20.04 LTS as the operating system.

## Requirements
- Ansible 2.10 or higher
- Access to three Ubuntu 20.04 LTS servers
- SSH access to each server with sudo privileges

### Usage

1. Clone this repository to your local machine:

		git clone https://github.com/tryingtobecoder58/es-ansible-installation

2. Modify the inventory.ini file to include the hostnames or IP addresses of your three servers.

3. Modify the elasticsearch.yml file to set the cluster name, JVM heap size, network host, and xpack security settings as desired.

4. Run the Ansible-Playbook
	
		ansible-playbook -i inventory.ini playbook.yml


### Configuration

The following variables can be set in the site.yml file to customize the Elasticsearch installation:

- cluster_name: The name of the Elasticsearch cluster. Default is mycluster.
- jvm_heap_size: The JVM heap size for Elasticsearch. Default is 2g.
- xpack_security_enabled: Whether to enable X-Pack security in Elasticsearch. Default is false.
- network_host: The network host to use for Elasticsearch. Default is 0.0.0.0.
- discovery_seed_hosts: A comma-separated list of seed hosts for Elasticsearch discovery. Default is ["es01", "es02", "es03"].
- Check the cluster health with below command.
		
		curl -XGET http://es02:9200/_cluster/health?pretty=true




To uninstall

	sudo apt-get --purge autoremove elasticsearch -y
	sudo apt-get remove --purge elasticsearch 
	sudo rm -rf /etc/elasticsearch
	sudo rm -rf /var/lib/elasticsearch
