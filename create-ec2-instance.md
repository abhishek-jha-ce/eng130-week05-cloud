# Creating an EC2 Instance

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
- General Purpose - the t2.micro instance, which we are using is a general purpose instance.
- Compute Optimized - When we need high performance processors. For e.g. high performance web servers, high performance computing (HPC), scientific modeling, dedicated gaming servers.
- Memory Optimized - Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory. For e.g. real-time big data analytics.
- Storage Optimized - Storage optimized instances are designed for workloads that require high, sequential read and write access to very large data sets on local storage. For e.g. database

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
