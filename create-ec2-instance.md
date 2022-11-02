# Creating an EC2 Instance
**Pre-requisite**
- We have to save our *.pem* file containing the key into the `.ssh` folder. `C:Users/username/.ssh`.
- Select the location as `Europe (Ireland)`, which is `eu-west-1` region. We will be working mostly from this location. 


**Step 1**: Log-in to Amazon Console

**Step 2**: Select EC2 Instance. We can select EC2 instance from 3 available options:

|Recently Used|From Service Blade|From Search Bar|
|:-:|:-:|:-:|
|![Recently Used](https://user-images.githubusercontent.com/110366380/199284774-f944e540-2d46-44eb-adce-d1b078dda311.png)|![Service Blade](https://user-images.githubusercontent.com/110366380/199284384-6f97fbe8-9843-493d-a6cf-276a82af7977.png)|![Search Bar](https://user-images.githubusercontent.com/110366380/199284565-8550e09c-e921-425b-aed6-2c56e1b355ef.png)|

**Step 3**: Scroll down and click on **Launch instance** button and select `Launch instance`.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199286440-3d3ab484-4d2a-4e72-9a91-1f76f505796d.png">
</p>

**Step 4**: We will have a option now to enter the details of the virtual machine.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199289836-4628c1b9-dd64-4591-9104-754b9e91a21a.png">
</p>

**Step 5**: We select the Amazon Machine Image, which we will use. It's the Operating System that we will be using for our Virtual Machine.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199291224-8e3da801-7f9d-4ce6-9349-ee8382b1796e.png">
</p>

Select this Image (AMI):

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199290608-c0dac4fa-a0b1-465f-ac0d-dcad24a0d8b1.png">
</p>

**Step 6**: Select the instance type we require. AWS provides wide selection of intance types. It is optimized to fit different use case.

- Instance types comprise different combination of CPU, memory, storage and networking capacity.
- It gives us the flexibility to choose the appropriate mix of resources for our application.
- Each instance type includes one or more instance size, allowing us to scale our resources as per our workload.
- Most importantly, it shows us how much we will be charged.

  
<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199291775-2d18eb25-fed1-4875-963e-c6ec5b2b7a70.png">
</p>

The most commonly used instace types are:
- **General Purpose** - the t2.micro instance, which we are using is a general purpose instance.
- **Compute Optimized** - When we need high performance processors. For e.g. high performance web servers, high performance computing (HPC), scientific modeling, dedicated gaming servers.
- **Memory Optimized** - Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory. For e.g. real-time big data analytics.
- **Storage Optimized** - Storage optimized instances are designed for workloads that require high, sequential read and write access to very large data sets on local storage. For e.g. database

**Step 7**: We select a key-pair login. This is to make sure we have the access to our `.pem` file before launching our instance. The `.pem` file is stored in the `.ssh` folder.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199297534-612f4da5-5b23-42c3-9bca-016162b12d9b.png">
</p>

**Step 8**: We select a network setting. We select 3 main things in this step.

1. Select the Security Group (Firewall) - We create a new SG, where we add all the rules.
2. Select where do we allow `SSH Traffic` from - In this case, we select our IP, so only we can connect to our instance.
3. Select *Allow HTTP traffic from the internet* - To let everyone access our public ip for the VM.

If we're selecting any existing `Security Group` we don't have to repeat point 2 & 3 agin, as it will be already added to the security rules.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199298943-8e353fa9-607b-4f05-958b-cd3e04e52308.png">
</p>

**Step 9**: Finally, we configure the storage we require for our `VM` or the `EC2 Instance`.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199299239-090fdb2c-c9bb-4c33-8492-1afaea4ef234.png">
</p>

**Step 10**: We can Launch our instance now. If successfully launched, we will see a confirmation screen with the `instand id`, which we can view in details.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199299908-e86fed64-d6c1-466a-b9c7-cf0cb907159f.png">
</p>

**Step 11**: We can press the `Connect` button to see the options that we have to connect to the `EC2 instance`.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199300766-eee7b69b-9c01-4d53-a0f8-50f693e4e4ed.png">
</p>

- From the terminal we can connect to our instance using ssh:

```
ssh -i "eng130.pem" ubuntu@ec2-3-250-67-179.eu-west-1.compute.amazonaws.com
```

Now we are connected to our `ec2 instance`. We can install `nginx`:

```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt install nginx
```

After installing `nginx`, if we go to the browser and type our public `ip address` we can see the following:

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/199304091-b174e663-fcc9-45d6-bda1-ee3eafaaa7d8.png">
</p>

### Setting up reverse proxy with `nginx`

We already have `nginx` installed in our `Virtual Machine` or the `EC2 Instance`. We can setup a reverse proxy by modifying the `deault` file.

```
$ sudo nano /etc/nginx/sites-available/default
```

- Inside this file, find the `location` block and modify it as follows:

```
   location / {
        proxy_pass http://localhost:8080; #Change this to the port of your application
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```
- Save the file, and test the configuration.

```
$ sudo nginx -t

```
- If there is no syntax error, we should receive this message.

```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
- Restart `nginx`, for the changes to take effect.

```
$sudo systemctl restart nginx
```

- Since we haven't hosted anything yet, we will see the following message in the browser.

![image](https://user-images.githubusercontent.com/110366380/199454016-def7450e-e04c-446d-8e15-11bed06da912.png)


