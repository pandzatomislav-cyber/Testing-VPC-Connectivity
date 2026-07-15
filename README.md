<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-connectivity)

**Author:** Tomislav Pandza  
**Email:** pandza.tomislav@gmail.com

---

## Testing VPC Connectivity

![Image](http://nextwork.ai/elated_teal_vibrant_raccoon/uploads/aws-networks-connectivity_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

A Virtual Private Cloud (VPC) is a logically isolated section of a public cloud, such as AWS, where users can launch and manage resources securely. It combines the scalability of public cloud infrastructure with the isolation and control of a private network.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to test the connectivity between my instances/computers through ping command and curl to fetch html content from a website.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how correct your setup needs to be when it comes what inbound and outbound traffic you allow and how fragile it can be.

### This project took me...

This project took me about 2h in total however with more practise I belive one can do it faster.

---

## Connecting to an EC2 Instance

Connectivity is all about how well different parts of one's network talk to each other and with external networks. It's essential because connectivity is how data flows smoothly across your network, powering everything from simple web hosting on the Internet to complex operations

My first connectivity test was whether I could connect two of my instances to talk to each other

![Image](http://nextwork.ai/elated_teal_vibrant_raccoon/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is a shorter way of connecting your SSH with your instances.

My first attempt at getting direct access to my public server resulted in an error, because my security group's inbound traffic was only allowed to http and not SSH.

I fixed this error by adding SSH to the inbound traffic of the securuty group. Normally we would not limit it to all traffic but to the exact block of CIDR IP addresses which EC2 Instance Connect would use to restrict inboud SSH traffic to that block exactly.

![Image](http://nextwork.ai/elated_teal_vibrant_raccoon/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a common computer network tool used to check whether your computer can communicate with another computer or device on a network.

The ping command I ran was ping 10.0.0.19, which is the private IPv4 address on my EC2 instance.

The first ping actually returned successful communication  between the instances however in case it only displayed the message gone out, you need to edit your inbound rules on your private security group in the VPC console.

![Image](http://nextwork.ai/elated_teal_vibrant_raccoon/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I did not have to troubleshoot this one particulary as the connectivity seemed to be running just fine. In case you do have an error, you need to navigate to security groups in the VPC page, edit the inbound traffic to type - All ICMP IPv4 and your surce: Custom - Public Network Security Group

![Image](http://nextwork.ai/elated_teal_vibrant_raccoon/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

Curl is a call like ping is. Where ping checks if one computer can contact another (and how long messages take to travel back and forwth), curl is used to transfer data to or from a server. That means on top of checking connectivity, you can use curl to grab data from, or upload data into other servers on the internet

I used curl to test the connectivity between an https server and my instance

### Ping vs Curl

Ping and curl are different because ping is a command used for seeing the communication between two computers, curl is used to transfer data to or from a server.

---

## Connectivity to the Internet

I ran the curl command "curl https://nextwork.ai" and this showed the html content of the website on which I am actually practising right now.

![Image](http://nextwork.ai/elated_teal_vibrant_raccoon/uploads/aws-networks-connectivity_8ee57662)

---

---
