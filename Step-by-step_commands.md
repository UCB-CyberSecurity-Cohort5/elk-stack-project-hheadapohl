# Day 1:

Step1: Create New Virtual Network in different region
![alt_text](images/Day1_Step1_Create_Vnet.png "image_tooltip")

Step1: Create Peer Connection Between Vnets
![alt_text](images/Day1_Step1_Vnet_Peer_Connection_Established.png "image_tooltip")

Step2: Log into ansible container in JumpBox
![alt_text](images/Day1_Step2_attach_ansible_container.png "image_tooltip")

Step2: Get ssh public key from ansible container
![alt_text](images/Day1_Step2_get_ansible_ssh_key.png "image_tooltip")

Step2: Create new ELK-SERVER Vm
![alt_text](images/Day1_Step2_create_elk_vm_settings.png "image_tooltip")

Step2: Ensure jumpbox can connect to ELK-SERVER
![alt_text](images/Day1_Step2_ELK-SERVER_inbound_rule.png "image_tooltip")

Step2: Test VM connection
![alt_text](images/Day1_Step2_test_vm_ssh_connectivity.png "image_tooltip")

Step3: Modify ansible hosts file to create [elk] group with ELK-SERVER’s IP
![alt_text](images/Day1_Step3_modify_ansible_hosts.png "image_tooltip")

Step3: Create ansible playbook to install elk stack on ELK-SERVER
![alt_text](images/Day1_Step3_install-elk_yml.png "image_tooltip")

Step4: Run the install-elk playbook by running **ansible-playbook install-elk.yml**
![alt_text](images/Day1_Step4_run_install_elk_playbook.png "image_tooltip")

Step4: SSH from ansible to ELK_SERVER and use sudo docker ps to verify that the elk container is running
![alt_text](images/Day1_Step3_check_elk_running.png "image_tooltip")

Step5: Add inbound rule to NSG to allow access to Kibana on port 5601
![alt_text](images/Day1_Step5_allow_port_5601.png "image_tooltip")

Step5: Log into Kibana on port 5601 from the local machine. Success!
![alt_text](images/Day1_Step5_successful_kibana_webpage.png "image_tooltip")


# Day 2

Part 2: create and edit filebeat-config.yml



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.png "image_tooltip")


Part3: use touch to create filebeat-playbook.yml



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.png "image_tooltip")


Part3: Write YAML playbook script to install and run filebeat on hosts [webservers], enabling restart on reboot

Part3: Verify that playbook ran successfully

Part4: Verify filebeat module status in Kibana

Part5: Modify metricbeat-config file to have correct hosts

Part5: Create metricbeat-playbook.yml to install and configure metricbeat on webservers



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image7.png "image_tooltip")


Part5: Run ansible-playbook metricbeat-playbook.yml and verify playbook ran without error

Part5: On metricbeat installation page on ELK server, verify that metricbeat is installed and running correctly



<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image8.png "image_tooltip")

