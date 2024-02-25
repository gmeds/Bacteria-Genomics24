# What we will cover
-**Understanding EC2:** Virtual servers, instances, elasticity, on-demand provisioning
- **EC2 Instance Types:** Diverse instance families for different workloads
- **EC2 Pricing Models:** On-demand, Spot, Reserved Instances, cost optimization
- **Hands-On Lab 1:**Creating Your First EC2 Instance
- **Connecting to Instances:** SSH (Linux/Mac), RDP (Windows)
- **EC2 Configuration:** Installing software, application deployment
- **EBS (Elastic Block Store):** Persistent block-level storage, volume types (SSD, HDD, provisioned IOPS)

## Understanding EC2: Virtual servers, instances, elasticity, on-demand provisioning

EC2 is like having your own powerful computer in the cloud – a virtual server! We call these virtual servers 'instances.' It's like renting a computer instead of buying one outright.

Now, here's why EC2 is so cool:

**Elasticity:** Need more power? Need less? You can scale your instance up or down in minutes. This flexibility is what we call 'elasticity.

**On-demand provisioning:** Think of it as pay-as-you-go computing. Spin up an instance when you need it, and shut it down when you don't. You only pay for what you actually use."

**EC2 Instance Types:** Diverse instance families for different workloads

**What are instance types?**

While working with EC2s, one of the things we will have to work with is instance types.

Amazon EC2 instance types are basically predefined configurations of CPU, memory, storage, and networking resources that you can launch as a virtual server in the AWS cloud.

Think of them like computer models - you have options like laptops, desktops, and servers to choose from. EC2 instance types are similar - they come in different sizes to suit different computing needs.

"EC2 isn't one-size-fits-all. It offers a whole bunch of instance types, like different flavors designed for specific needs.

When picking an instance type, you will need to handle several tradeoffs and understand the nature of the work you are involved in:

Here is an overview of the instance types:

![image](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/ff89ebd4-89b3-4bd7-ad8f-accb03cbe838)

_Source: Pradeep, P., Aggarwal, P., Zaman, S. H. B., Sakauchi, T., Demos, W., & Struble, C. (2010). Discovering Drugs on The Cloud._


## Hands-On Lab 1: Creating Your First EC2 Instance

Log into your AWS console and go to the EC2 dashboard.

1. Put your cursor at the search button, then type "ec2": This will bring you AWS services with the name ec2.
2. Click on the one write EC2

![creatingec2insatnce](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/05bf073a-655d-4ce7-be72-2ca391826cbd)

This will bring you an interface that looks like the one below:

![image](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/ed81cd39-4e86-404b-8f79-1a6feda28122)

3. Click on the "Launch Instance" button.
4. Choose an Amazon Machine Image (AMI) - this contains the operating system (Linux, Windows) and software. Select one that matches your needs.

   ![creatingec2insatnce(1)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/3e0fa6ca-3032-453b-9aa2-351016f75458)

6. Let us first explore the kinds of AMI available. Click on **browse more AMIs** button, which will bring you to a page like this:
You can still choose the available AMIs or look for desired AMIs in the AWS marketplace AMIs or the **community AMIs.** Now, you will most likely be choosing for community AMIs
These are those that might contain pre-installed tools such as those related to bioinformatics. For instance, search for **CHENLAB-PUBLIC** in the community AMIs. You may work with it
if you want. For now, we will work with quickstart AMIs, just to maintain the idea of building your own staff from the scratch.
7. Look for the Ubuntu AMI, and click select.
8. Next, let us choose an instance type. This will depend on your workload and budget. For the demo, we will work with t2 instance type. But for data analysis,
    we will work with a larger and more efficient instance type
   
![creatingec2insatnce(3)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/26665d5c-1bfe-4317-81bd-bf21a6bd6528)

 9. Once you have chosen an instance, proceed to create key pairs for login. You will download either a **.pem** file or **.ppk** file. This will allow us to log into our ec2 instance as we will see:

     ![creatingec2insatnce(4)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/9540dc3e-54fa-41a5-adcc-c83bcd1cf119)

 11. Next, configure the network settings. In most cases, you would just leave the settings as they are. Just in case you choose to edit, these are the standard settings

     ![creatingec2insatnce(5)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/49dda647-5ff0-4697-a93e-a3c2115f0e91)

13. Next, we will do storage configurations. This allows you to allocate initial storage to your instance. For the free tier, you can allocate up to 30gbs for your instance.
    AWS will charge you if you go beyond that.
14. With all these settings, you can look at the summary, and when satisfied, click 

   ![creatingec2insatnce(7)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/0a7b8717-3458-4583-b087-573b6b5e5965)

14. With the instance successfully launched, you will be taken to a page that will allow you to view all your instances. Here, you will see that the instance is running.
15. If you checkbox this instance, you should see the instance details, including the public IP address which will be important when logging in.

## Logging into an EC2 instance
1. Since we have created the EC2 instance, we can now log in. We will do this using the AWS cloud shell. Look into the AWS search button and search for aws **cloud shell.**
   Right-click on it and open it in a new tab, at least this is how I prefer. You can alternatively open it in the current tab. No harm.
   
![creatingec2insatnce(8)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/4b1fb400-be99-445d-ac78-94e89d797db7)

3. With the targeted instance checked, click on the **connect** button to bring you to a page that tells you how to **ssh** into the instance.
   There are multiple ways to connect to the ec2 instance. For this lecture, we are more interested in using the ssh client. Click on this.
   AWS provides explicit steps on how to log in: Look below:

   ![creatingec2insatnce(9)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/8f73ebbd-1564-4903-9ca9-0898934f9f1c)
   
5. Let us now head to our Cloudshell to log in. First, upload the key pairs you downloaded earlier. Look at step 9 above. Head over to the cloud shell and upload this file.
   The easiest way to do this is, when in your shell, to click on the **action** drop-down button, and then look at the option for **upload file**.
   Confirm that the file is uploaded by keying in **ls**
6. with the key pairs file uploaded, make the file into an executable by running.
7. Finally, connect to the instance by running **ssh -i "keypairs.pem" username@Public-IPv4-address.compute-1.amazonaws.com**
   In our case, this would be something like ssh -i "b24.pem" ubuntu@ec2-35-173-190-180.compute-1.amazonaws.com

   ![creatingec2insatnce(10)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/a6b23df5-7bfb-4acf-a01a-124f2e03fd20)


## EBS (Elastic Block Store): Persistent block-level storage, volume types (SSD, HDD, provisioned IOPS)

"Think of EBS as super-flexible hard drives for your EC2 instances.  They come in different flavors:
- SSD (Solid State Drives): Super snappy, great for high-performance workloads.
- HDD (Hard Disk Drives): Classic and cost-effective for bulk storage.
- Provisioned IOPS: For when you need super-precise performance guarantees.

EBS is what lets your data persist even if you shut down your instance."
### Creating an EBS volume
1. To create an EBS volume, at the panel where you have your instance, look at the far right, search for the label **Elastic Block Store**, and then click on **volumes**.
2. You will be taken to a page that will allow you to create volumes. Look for the button **Create volume** and click on it.

![creatingec2insatnce(11)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/5b1a9e90-22b2-4675-9503-bdc48dccc9d2)

4. Fill out the details you want for this volume including volume type (just leave as general purpose), volume of space you need, etc. For this demo, just set the volume at 100G.
   That would be fine.
   
   **NOTE: Ensure the Availability Zone is set the same as the EC2 instance you are going to attach the volume to.**
   
6. **Tags** are _optional_ but you can always set them to easily identify this volume in future use.
7. Finally, click on **Create** and wait as the volume is being created.

   ![creatingec2insatnce(12)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/8e693c17-806a-4ec1-81d2-c295e855484e)

8. Once the volume is created, it will be labeled as **available**. You can the attach it to an ec2 instance. To do this;
9. Click on the **Actions** drop-down button, then click on the **Attach volume** option, which will take you to the **Attach volume** page.

   ![creatingec2insatnce(13)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/40d0e918-239c-4525-a060-bce7429d941f)

10. Select the **instance** to attach to this volume, then click **Attach volume**. If successful, the volume state should change from _available_ to _in-use._

![creatingec2insatnce(14)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/baf03d95-773a-4e69-adaf-5c812ddeafca)

### Mounting an EBS volume
Creating and attaching the volume are just initial steps. To use this volume, we will need to mount it on the ec2 instance.

Start by confirming the disks available to the ec2 instance.

Use the command `lsblk` to get the list of available disks and whether (including where) they are mounted. Now, look for the particular volume that we created. 
Look through the list provided, for a disk of volume 100G (this is what we created) and note the device name. In our case, this should be `xvdf`
Check whether this volume has some data in it by running `sudo file -s /dev/xvdf` where xvdf is the name of our device.
If the command returns something like this `/dev/xvdf: data` it means that the disk is **empty.** We can now mount it.

#### Steps to mounting EBS volume
1. Begin by formatting the disk to the ext4 filesystem using the command `sudo mkfs -t ext4 /dev/xvdf`. In future, make sure you DO NOT DO THIS for an existing volume as you will
   end up erasing the data.
2. Make a directory where we will mount the volume using the command `sudo mkdir /mnt/volume1`
3. Mount the volume to the above-created directory using the command `sudo mount /dev/xvdf /mnt/volume1`
4. cd into the directory and check the disk space to verify that the mounting is done. Use the command `df -h .`
5. At this point, the drive is owned by the root and not user. We will want to change ownership of the drive so that you can change the contents of the drive.
   Use this command `sudo chown -R ubuntu /mnt/volume1`
6. In the end, if you want to unmount this volume, you can use the command `sudo umount /dev/xvdf`

   ![creatingec2insatnce(15)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/886a0cb2-e0a2-456a-a062-855c399163a1)

# Closing/stopping an EC2 instance
Without stopping an ec2 instance, Amazon will charge you for it. Ensure you stop any instance you were working with before logging out. To do this, follow the following steps:
1. Checkbox the instance you wish to stop, head over to the instance state drop-down button, and click on it. Click on the option to stop the instance.
2. Read the warning, then click on stop. The warning implies that regardless of stopping the instance, you will be charged for any associated resources, including the volume we attached earlier. So, we will need to address this if we do not want to incur the extra charges.
3. You can even terminate this instance if you no longer want to use it in the future. By terminating the instance, you delete any associated volume.
   ### Detaching an EBS volume
   Let us address the issue of EBS volume, once an EBS is stopped. The best route is to detach this volume. Head over to volumes, in the Actions drop-down button, click on detach volume. You can
   then delete this volume in the same panel.

<h1 align="center">THANKS FOR READING.</h1>

   <h3 align="center"> If you enjoyed the lecture, you can buy me coffee to support me in creating more lectures.</h3>
