# Implementing VPC for our App

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/200374233-f7d42141-a451-4c8a-b30d-6dfb65b9f9cb.png">
</p>

### Step 1: Create a VPC

Amazon Virtual Private Cloud (Amazon VPC) enables us to launch AWS resources into a virtual network that we've defined. This virtual network closely resembles a traditional network that we operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

##### To Create a VPC

Choose the following settings to setup the VPC:

**VPC Settings**
- Click on `Create VPC` option, which can be found after you select VPC service.
- For Settings, we select `VPC Only`
- Provide a Name tag e.g. `eng130-abhishekjha-vpc`
- For IPv4 CIDR Block - select `IPv4 CIDR Manual Input` and enter `10.0.0.0/16`
- Make sure to select `No IPv6 CIDR Block`
- Leave the Tenency as `default`.  
- Finally click on `Create VPC`. It will create a new VPC with the provided name.

### Step 2: Create a Internet Gateway

An Internet gateway is used to transfer communications between an enterprise network and the Internet. To create a Internet Gateway:

- Click on `Internet Gateways`.
- Provide the Name Tag
- Click on `Create Internet Gateway`.

#### Step 2.1: Attach the Internet Gateway to the VPC

- After the `Internet Gateway` is created, we will see an option to attach it to the VPC. 
- If no option present, we can select `Actions` and then `Attach to a VPC`.
- Click on `Attach Internet Gateway` to attach it. The state of the gateway should be showing as `Attached`.

### Step 3: Create a Subnet

- To create a subnet, click on `Subnets` on the left blade, and then click on `Create Subnet`.
- Select the VPC we created earlier.
- Give the subnet a name, and let the availibility zone as `no preference`.

We are creating 2 subnet here:

  #### Public Subnet
  ```
  In the IPv4 CIDR Block, use `10.0.3.0/24`
  ```
  
  #### Private Subnet
  ```
  In the IPv4 CIDR Block, use `10.0.15.0/24` 
  ```
  
- Click on `Create Subnet` to complete the process.

### Step 4: Create a Route Table

- To create a route table, click on `Route tables`
- Give it a Name (append public and private to its name to make sure we don't get confused later).
- Select the earlier created VPC. 
- Click on `Create route table`.

*Note*: The `route table` is created but it doesn't contains any information yet.

#### Step 4.1: Add `routing rules` to the table

- Click on `Edit routes` selecting the required route.
- One route will be already present inside, which is for the `VPC`. It will be the same IP as mentioned while createing the `VPC` i.e. `10.0.0.0/16`

#### Public Subnet
- We need to give access to the internet for the public subnet, so we add:

```
Destionation: 0.0.0.0/0 - For everyone to access.
Target: Internet Gateway - As soon as we select it, It will populate it with the Internet Gateway that we created.
```

#### Private Subnet
```
Destionation: 10.0.3.0/24 - For everyone to access.
Target: Instance (App) - As soon as we select it, It will populate it with the Instance ID. // NW
```


#### Step 4.2: Associate the `Route table` to the respective `Subnet`
- Click on `subnet association` tab at the bottom half of the page.
- Select the preferred subnet.
- Click on `Save association` to save it.


### Step 5: Create an EC2 Instance within the VPC.

- We already have the image (AMI) for the `app` and `database` Virtual Machine available. We will reuse the same image.
- Rest all step is same as creating the instance.
- Edit the network settings.
- Select the Virtual Private Cloud (VPC), we created earlier.
- Select the respective `subnets`.
- Create a new Security Group for each subnet.


#### Security Group for App: 

*Note*: The `auto-assign public IP` should be enabled for the public subnet.

- SSH for Port 22 from `My IP`.
- HTTP access for Port 80 from `0.0.0.0/0`.
- Custom TCP for Port 3000 from `0.0.0.0/0`.

#### Security Group for Database:

*Note*: The `auto-assign public IP` should be disabled for the private subnet.

- Custom TCP for Port 27017 from `10.0.X.0/24`. X=3 in this instance. To allow Mongodb traffic from the app (public subnet).
- SSH for Port 22 from `My IP`.

### To connect the app to database

- In the git bash terminal, SSH into the app.

- Create Environment Variables:
```
ubuntu@ip-10-0-3-29:~$ export DB_HOST=mongodb://10.0.3.29:27017/posts

The IP address should match to the one on the left. It can change for every launch of the instance.
```
