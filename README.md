# WPCloudFormation
CloudFormation template for Basic WordPress setup on AWS. 

# Objective

Use CM tools such as Puppet, Ansible, or Chef to automate the installation of basic Drupal or WordPress. Setup a sample site. Automate the solution using CloudFormation template.

# Deliverable

Create CloudFormation template that should setup a VPC, create subnets, launch a CM instance, and configure a Web Server for basic Drupal or Wordpress setup. 

# Solution

The CloudFormation template creates a VPC, 1 Public Subnet, 1 Web Server Instance in the Public Subnet, Security Group for the Instance, and required components to connect to the internet ie. InternetGateway, RouteTables, Route. 

I decided to use Ansible to provision the Web Server Instance, mainly because i have never worked with the other CM tools. 

There is no CM instance because the Ansible Playbook is run locally, after instance creation. I did this by using a shell script that installs Ansible, and clones the Ansible repo to install and start a WordPress server. I passed the shell script to the Web Server instance using the User Data parameter, in CloudFormation.  

My justification behind not using a CM instance to provision the WebServer was,  It's more cost efficient to have just 1 server running, especially for a simple Wordpress site. However, if there were many WebServer instances and they all needed to be configured, especially when using a ASG, i would definitely use a dedicated CM instance on a private subnet.

I also did not use dedicated Database server, again i did not think it was nessecary for a simple wordpress site, especially if its a simple blog or static site.  
