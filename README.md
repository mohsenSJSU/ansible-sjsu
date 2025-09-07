# Individual Assignment

Configure two VMs, VM1 and VM2 either on your own hardware, or in a cloud environment. Configure Ansible to deploy a webserver on VM1 and VM2 on port 8080 with a web page that is accessible from a web browser, and displays the message: “Hello World from SJSU-X” where X is 1 or 2 depending on which webserver instance, VM1 or VM2.
Include in the Ansible playbook, plays to deploy and un-deploy the webserver resources

Submit a Word document, with screenshots showing your work, and a demo, and all ansible code/scripts via github

# MohsenMinai - 019133075 - SJSU - Enterprise Software Platforms - Ansible HW — Two VMs,using Nginx on port 8080

# Overview
Ansible playbook deploys Nginx on two Ubuntu VMs and serves (using terminal only):
- VM1(192.168.64.10) → “Hello World from SJSU-1”
- VM2(192.168.64.11) → “Hello World from SJSU-2”
- Listen port: 8080. Includes deploy and un-deploy plays.

# Files used
- ansible-sjsu/
-  ansible.cfg
-  inventory.ini
-  site.yml
-  templates/
  -  hello.conf.j2
  -  index.html.j2
-  host_vars/
  -  vm1.yml
  -  vm2.yml

# Method
To complete this assignment, 
- Create two Ubuntu VMs (I used Multipass) and confirm you can SSH into them with your key (create key if needed).
- Install Ansible (brew install ansible), clone this repo, and update hosts.ini with the IPs of vm1 and vm2 plus ansible_user=ubuntu and your key path.
- Verify connectivity with ansible -i hosts.ini web -m ping, then deploy with ansible-playbook -i hosts.ini site.yml --tags deploy.
- This installs Nginx, renders the templates, and serves the pages on port 8080; check in a browser at http://<vm-ip>:8080 (or curl).
- To undeploy, run ansible-playbook -i hosts.ini site.yml --tags undeploy.
