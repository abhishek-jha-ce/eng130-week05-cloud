# Implementing VPC for our App

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

After the `Internet Gateway` is created, we will see an option to attach it to the VPC. If no option present, we can select `Actions` and then `Attach to a VPC`.
