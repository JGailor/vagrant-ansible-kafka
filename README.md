# Purpose

A base setup for creating a running virtual machine using Vagrant and provisioning[Apache Kafka](http://kafka.apache.org/) on the VM using Ansible.

# Getting Started

1. [Install Vagrant](https://docs.vagrantup.com/v2/installation/index.html)
2. [Install Ansible](http://docs.ansible.com/intro_installation.html#installation)
3. Open a terminal
4. ````git clone git@github.com:JGailor/kafka-ansible-vagrant.git````
5. ````cd kafka-ansible-vagrant````
6. ````vagrant up````

You should now have a provisioned VM running ZooKeeper and Kafka

# Kafka

What is Apache Kafka? According to the developers, "Apache Kafka is publish-subscribe messaging rethought as a distributed commit log".  It was developed at LinkedIn and powers big parts of their data infrastructure.  The project page lists numerous use cases, but one of my favorites is a replayable message queue.  What this means is that you can go back in the queue after processing messages to reprocess them again. As a concrete example: Imagine you are ingesting unstructured data from web crawling.  Unbeknownst to you the source has changed for one of the sites you crawl, and your parsers are broken.  With Kafka, your client can identify that bad parsing is occurring, then rewind it's position in the queue after it's been fixed and reprocess the messages it was unable to before.  Additionally, if you were interested in running alternative experiments on the queue ("topic" in Kafka nomenclature), you can run parallel code against the queue, and measure the results of each experiment against your control to test for performance, quality, etc.
