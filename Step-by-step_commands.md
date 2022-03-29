# Day 1:

### Step 1: Create New Virtual Network in different region
![alt_text](images/Day1_Step1_Create_Vnet.png "image_tooltip")

### Step 1: Create Peer Connection Between Vnets
![alt_text](images/Day1_Step1_Vnet_Peer_Connection_Established.png "image_tooltip")

### Step 2: Log into ansible container in JumpBox
![alt_text](images/Day1_Step2_attach_ansible_container.png "image_tooltip")

### Step 2: Get ssh public key from ansible container
![alt_text](images/Day1_Step2_get_ansible_ssh_key.png "image_tooltip")

### Step 2: Create new ELK-SERVER Vm
![alt_text](images/Day1_Step2_create_elk_vm_settings.png "image_tooltip")

### Step 2: Ensure jumpbox can connect to ELK-SERVER
![alt_text](images/Day1_Step2_ELK-SERVER_inbound_rule.png "image_tooltip")

### Step 2: Test VM connection
![alt_text](images/Day1_Step2_test_vm_ssh_connectivity.png "image_tooltip")

### Step 3: Modify ansible hosts file to create [elk] group with ELK-SERVER’s IP
![alt_text](images/Day1_Step3_modify_ansible_hosts.png "image_tooltip")

### Step 3: Create ansible playbook to install elk stack on ELK-SERVER
![alt_text](images/Day1_Step3_install-elk_yml.png "image_tooltip")

### Step 4: Run the install-elk playbook by running **ansible-playbook install-elk.yml**
![alt_text](images/Day1_Step4_run_install_elk_playbook.png "image_tooltip")

### Step 4: SSH from ansible to ELK_SERVER and use sudo docker ps to verify that the elk container is running
![alt_text](images/Day1_Step3_check_elk_running.png "image_tooltip")

### Step 5: Add inbound rule to NSG to allow access to Kibana on port 5601
![alt_text](images/Day1_Step5_allow_port_5601.png "image_tooltip")

### Step 5: Log into Kibana on port 5601 from the local machine. Success!
![alt_text](images/Day1_Step5_successful_kibana_webpage.png "image_tooltip")


# Day 2

### Part 2: create and edit filebeat-config.yml

![alt_text](images/Day2_Part2_edit filebeat_config_yaml.png "image_tooltip")

### Change hosts to 10.1.0.4:9200
![alt_text](images/Day2_Part2_filebeat-config_changes.png "image_tooltip")

### Part 3: use touch to create filebeat-playbook.yml
![alt_text](images/Day2_part3_create_filebeat-playbook-yaml.png "image_tooltip")

### Part 3: Write YAML playbook script to install and run filebeat on hosts [webservers], enabling restart on reboot
![alt_text](images/Day2_part3_filebeat-playbook_yaml.png "image_tooltip")

### Part 3: Verify that playbook ran successfully
![alt_text](images/Day2_part3_run_filebeat-playbook.png "image_tooltip")

### Part 4: Verify filebeat module status in Kibana
![alt_text](images/Day2_Part4_verify_filebeat_installation.png "image_tooltip")

### Part 5: Modify metricbeat-config file to have correct hosts (10.1.0.4:5601)
![alt_text](images/Day2_part5_modify_metricbeat-config.png "image_tooltip")

### Part 5: Create metricbeat-playbook.yml to install and configure metricbeat on webservers
![alt_text](images/Day2_Part5_metricbeat-playbook_file.png "image_tooltip")

### Part 5: Run ansible-playbook metricbeat-playbook.yml and verify playbook ran without error
![alt_text](images/Day2_part5_verify_playbook_installation.png "image_tooltip")

### Part 5: On metricbeat installation page on ELK server, verify that metricbeat is installed and running correctly
![alt_text](images/Day2_part5_test_metricbeat_in_kibana.png "image_tooltip")

## Congratulations! You have successfully replicated this project deployment.

