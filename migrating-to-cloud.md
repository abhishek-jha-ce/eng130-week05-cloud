# Migrating to the Cloud

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199682202-701040fe-b8b0-4677-a993-feeb3c888a12.png">
</p>

## Copying Local file to EC2 Instance

We can copy our local files to our EC2 Instance using `rsync` or `scp` commands.

- `rsync` - It stands for remote sync. It is a remote and local file synchronization tool. It uses an algorithm to minimize the amount of data copied by only moving the portions of files that have changed.
- `scp` - It stands for secure copy. It copies files or directories between a local and a remote system or between two remote systems. We can use this command from a remote system (after logging in with the ssh command) or from the local system. The scp command uses ssh for data transfer.

We transfer our data using `scp` because it is more **secure**. We navigate to our ssh folder and use the following commands.

```
scp -i "eng130.pem" -r <full path of local folder> ubuntu@<public-ip-address>:/home/ubuntu/

Example:
scp -i eng130.pem -r /c/Users/abhis/Downloads/app/ ubuntu@ec2-34-245-181-47.eu-west-1.compute.amazonaws.com:/home/ubuntu
```

*Note*: The default location for EC2 is `/home/ubuntu`

## Creating an instance using Automation Script

- To create an instance: [Creating an Instance](create-ec2-instance.md)
- To Use an automation script, while creating the instance, select Advanced Option, scroll down and in the User Data section add the bash script.

<p align="center">
  <img src="">
</p>

*Note*: This script will only run when creating the instance. It can't be accessed later.


