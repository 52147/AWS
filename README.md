# AWS
## introduction to Amazon Web Services
- key value of AWS: pay for what you need.
### cloud computing:
 - 1. on-demand delivery
 - 2. undifferentiated heavy lifting of IT
 - 3. pay as you go pricing
### client server model:
  - a client can be a web browser or desktop application that a person interacts with to make requests to computer servers.
  - A server can be services such as Amazon Elastic compute cloud(Amazon EC2), a type of virtual server.

  - 3 types of cloud computing deployment model:
  
    - 1. could -based deployment
         - run all parts of the applications in the cloud
         - migrate existing applications to the cloud
         - design and build new applications in the cloud

         - for example, a company might create an application consisting of virtual servers, ‎database, and networking components that are fully based in the cloud.
         
    - 2. on-premises deployment(private cloud deployment)
         - deploy resources by using virtualization and resource management tools
         - increase resource utilization by using application management and virtualization technologies      
         - virtualization: 
            - is the creation of a virtual version of something, such as an operating system (OS), a server, a storage device or network resources.
            - virtualization uses software that simulates hardware functionality to create a virtual system
            - For example, allow it organizations to operate multiple operating systems, more than one virtual system and various applications on a single server.
            - The benefits of virtualization include greater efficiencies and economies of scale.
         - for example,
you might have applications that run on technology that is fully kept in your on-premises data center.
         - Though this mode is much like legacy IT infrastructure, its incorporation of application management and virtualization technologies helps to increase resource utilization.
       - 3. hybrid deployment
         - connect cloud-based resources to on-premises infrastructure
         - integrate cloud-base resources with legacy IT applications

         -	In a hybrid deployment, cloud-based resources are connected on-premises infrastructure.
         -	For example, you have legay applications that are better maintained on premises,
         -	or government regulations require your business to keep certain records on premises.

         -	For example, suppose that a company wants to use cloud services that are automate bathch data processing and analytics.

         -	However, the company has several legacy applications that are more suitable on premises and will not be migrated to the cloud.

            -	With a hybrid deployment, the company would be able to keep the legacy applications on premises while benefiting from data and analytics services that run in the cloud.
## compute in the cloud
### Amazon Elastic Compute Cloud (Amazon EC2):
- multitenancy: Sharing underlying hardware between virtual machines.
- secure and separate from each other
- Amazon EC2 configurations:
  - Windows
  - Linux
  - Internal business apps
  - web apps
  - databases 
  - third-party software
- vertical scaling : you can make instances bigger or smaller whenever you need to.
- You control the networking aspect of Amazon EC2
- Compute as a service (Caas)
- with an Amazon EC2 instance you can use a virtual server to run applications in the AWS Cloud.
- You can provision and launch an Amazon EC2 instance within minutes.
- You can stop using it when you have finished running a workload.
- You pay only for the compute time you use when an instance is running, not when it is stopped or terminated.
- You can save costs by paying only for server capacity that you need or want.
### How Amazon EC2 works

1. Launch
   - First, you launch an instance. 
   - Begin by selecting a template with basic configurations for your instance. 
   - These configurations include the operating system, application server, or applications. 
   - You also select the instance type, which is the specific hardware configuration of your instance. 

   - As you are preparing to launch an instance, you specify security settings to control the network traffic that can flow into and out of your instance. Later in this course, we will explore Amazon EC2 security features in greater detail.

2. Connect
   - Next, connect to the instance. You can connect to the instance in several ways. 
   - Your programs and applications have multiple different methods to connect directly to the instance and exchange data. Users can also connect to the instance by logging in and accessing the computer desktop.

3. Use
   - After you have connected to the instance, you can begin using it. You can run commands to install software, add storage, copy and organize files, and more.
### Amazon EC2 instance
- each Amazon EC2 instance type is groupted under an instance family

- The different instance families in EC2 are general purpose, compute optimized, memory optimized, accelerated computing, and storage optimized.
- General purpose instances provide a good balance of compute, memory and networking resources, and can be used for a variety of diverse workloads like, web service or code repositories. 
- Compute optimized instances are ideal for compute intensive tasks like gaming service, high performance computing, or HPC, and even scientific modeling. 
- Similarly, memory optimized instances are good for memory intensive tasks. Accelerated computing, are good for floating point number calculations, graphics processing, or data pattern matching, as they use hardware accelerators. 
- And finally, storage optimized are good for, can you guess it?
- Workloads that require high performance for locally stored data.

#### Amazon EC2 instance types
- Amazon EC2 instance types are optimized for different tasks. 
- When selecting an instance type, consider the specific needs of your workloads and applications. 
- This might include requirements for compute, memory, or storage capabilities.

1. General purpose instances
- General purpose instances provide a balance of compute, memory, and networking resources. You can use them for a variety of workloads, such as:

   - application servers

   - gaming servers

   - backend servers for enterprise applications

   - small and medium databases

   - Suppose that you have an application in which the resource needs for compute, memory, and networking are roughly equivalent. You might consider running it on a general purpose instance because the application does not require optimization in any single resource area.

2. Compute optimized instances
   - Compute optimized instances are ideal for compute-bound applications that benefit from high-performance processors. Like general purpose instances, you can use compute optimized instances for workloads such as web, application, and gaming servers.

   - However, the difference is compute optimized applications are ideal for high-performance web servers, compute-intensive applications servers, and dedicated gaming servers. You can also use compute optimized instances for batch processing workloads that require processing many transactions in a single group.

3. Memory optimized instances
   - Memory optimized instances are designed to deliver fast performance for workloads that process large datasets in memory. In computing, memory is a temporary storage area. It holds all the data and instructions that a central processing unit (CPU) needs to be able to complete actions. Before a computer program or application is able to run, it is loaded from storage into memory. This preloading process gives the CPU direct access to the computer program.

   - Suppose that you have a workload that requires large amounts of data to be preloaded before running an application. This scenario might be a high-performance database or a workload that involves performing real-time processing of a large amount of unstructured data. In these types of use cases, consider using a memory optimized instance. Memory optimized instances enable you to run workloads with high memory needs and receive great performance.

4. Accelerated computing instances
   - Accelerated computing instances use hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs. Examples of these functions include floating-point number calculations, graphics processing, and data pattern matching.

   - In computing, a hardware accelerator is a component that can expedite data processing. Accelerated computing instances are ideal for workloads such as graphics applications, game streaming, and application streaming.

5. Storage optimized instances
   - Storage optimized instances are designed for workloads that require high, sequential read and write access to large datasets on local storage. 
   - Examples of workloads suitable for storage optimized instances include distributed file systems, data warehousing applications, and high-frequency online transaction processing (OLTP) systems.

  - In computing, the term input/output operations per second (IOPS) is a metric that measures the performance of a storage device. 
  - It indicates how many different input or output operations a device can perform in one second. 
  - Storage optimized instances are designed to deliver tens of thousands of low-latency, random IOPS to applications.

  - You can think of input operations as data put into a system, such as records entered into a database. An output operation is data generated by a server. 
  - An example of output might be the analytics performed on the records in a database. If you have an application that has a high IOPS requirement, a storage optimized instance can provide better performance over other instance types not optimized for this kind of use case.


### Amazon EC2 Auto Scaling

- If you’ve tried to access a website that wouldn’t load and frequently timed out, the website might have received more requests than it was able to handle. This situation is similar to waiting in a long line at a coffee shop, when there is only one barista present to take orders from customers.
- Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. By automatically scaling your instances in and out as needed, you are able to maintain a greater sense of application availability.

- Within Amazon EC2 Auto Scaling, you can use two approaches: dynamic scaling and predictive scaling.
- 1. dynamic scaling
     -Dynamic scaling responds to changing demand. 
- 2. predictive scaling
     - Predictive scaling automatically schedules the right number of Amazon EC2 instances based on predicted demand.


- adding Amazon EC2 Auto Scaling to an application, you can add new instances to the application when necessary and terminate them when no longer needed.

#### set tht Amazon EC2 instances capacity

- 1. set the minimum number of Amazon EC2 instances:
  - When you create an Auto Scaling group, you can set the minimum number of Amazon EC2 instances. The minimum capacity is the number of Amazon EC2 instances that launch immediately after you have created the Auto Scaling group. In this example, the Auto Scaling group has a - minimum capacity of one Amazon EC2 instance.

- 2. Next, you can set the desired capacity 
  - at two Amazon EC2 instances even though your application needs a minimum of a single Amazon EC2 instance to run.
   - Note: If you do not specify the desired number of Amazon EC2 instances in an Auto Scaling group, the desired capacity defaults to your minimum capacity.

- 3. set the maximum capacity: 
  - The third configuration that you can set in an Auto Scaling group is the maximum capacity. For example, you might configure the Auto Scaling group to scale out in response to increased demand, but only to a maximum of four Amazon EC2 instances.

  - Because Amazon EC2 Auto Scaling uses Amazon EC2 instances, you pay for only the instances you use, when you use them. You now have a cost-effective architecture that provides the best customer experience while reducing expenses.


### load balancer
- A load balancer is an application, takes in requests and routes them to the instances to be processed.
- Directing Traffic with Elastic Load Balancing


### Elastic Load Balancer:
  - Elastic Load Balancing is the AWS service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances.

  - A load balancer acts as a single point of contact for all incoming web traffic to your Auto Scaling group. 
  - This means that as you add or remove Amazon EC2 instances in response to the amount of incoming traffic, these requests route to the load balancer first. Then, the requests spread across multiple resources that will handle them. 
  - For example, if you have multiple Amazon EC2 instances, Elastic Load Balancing distributes the workload across the multiple instances so that no single instance has to carry the bulk of it. 

  - Although Elastic Load Balancing and Amazon EC2 Auto Scaling are separate services, they work together to help ensure that applications running in Amazon EC2 can provide high performance and availability.

- Example: Elastic Load Balancing
- 1. Low-demand period
  - Here’s an example of how Elastic Load Balancing works. Suppose that a few customers have come to the coffee shop and are ready to place their orders.

  - If only a few registers are open, this matches the demand of customers who need service. The coffee shop is less likely to have open registers with no customers. In this example, you can think of the registers as Amazon EC2 instances.


- 2. High-demand period
  - Throughout the day, as the number of customers increases, the coffee shop opens more registers to accommodate them. In the diagram, the Auto Scaling group represents this.
  - Additionally, a coffee shop employee directs customers to the most appropriate register so that the number of requests can evenly distribute across the open registers. 
  - You can think of this coffee shop employee as a load balancer.

## Glossary
### Amazon SNS
Amazon SNS is a publish/subscribe service. Using Amazon SNS topics, a publisher publishes messages to subscribers.

### Amazon SQS
Amazon Simple Queue Service (Amazon SQS) is a message queuing service. It does not use the message subscription and topic model that is involved with Amazon SNS.

### Amazon EC2 Auto Scaling
Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand.

### Elastic Load Balancing
Elastic Load Balancing is the AWS service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances.

### Region
A Region is a geographical area that contains AWS resources.
### Edge
An edge location is a data center that an AWS service uses to perform service-specific operations. Edge locations are examined in the next section of this module.
### AWS Outposts
AWS Outposts is a service that you can use to run AWS infrastructure, services, and tools in your own on-premises data center in a hybrid approach. AWS Outposts is explored later in this module.

### Comparing Amazon EBS and Amazon EFS
- Amazon EBS

  - An Amazon EBS volume stores data in a single Availability Zone. 

  - To attach an Amazon EC2 instance to an EBS volume, both the Amazon EC2 instance and the EBS volume must reside within the same Availability Zone.

- Amazon EFS

  - Amazon EFS is a regional service. It stores data in and across multiple Availability Zones.

  - The duplicate storage enables you to access data concurrently from all the Availability Zones in the Region where a file system is located. Additionally,on-premises servers can access Amazon EFS using AWS Direct Connect.
 

