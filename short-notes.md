# notes — 

**general-terms** —  
 `Idempotence` is the property of certain operations in mathematics and computer science,  
 whereby they can be applied multiple times without changing the result beyond the initial application.  

**security** —  
 To secure **`RPC`** connection:  
 1. set `spark.authenticate` to `true` to enable [`Spark`](https://spark.apache.org/docs/latest/security.html#authentication) to authenticate its internal `RPC` connections.  
 2. set `hadoop.rpc.protection` to `privacy` to enable [`Hadoop`](https://hadoop.apache.org/docs/r2.7.2/hadoop-project-dist/hadoop-common/SecureMode.html#Data_Encryption_on_RPC) to authenticate its internal `RPC` connections.  

 to enable **`debugging`** of the above encrypted RPC connections -  
 set this property in NodeManager, set it in the yarn-env.sh file:  
 `YARN_NODEMANAGER_OPTS="-Djavax.net.debug=all"`
 in `yarn-env.sh`  

 It requires `keys` for data `at-rest` encryption and `certificates` for data `in-transit` encryption  
 
 [**`Memory Encryption`**](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/data-protection.html) — 
 
  We can also encrypt data while it's in `RAM`, and it's possible in couple of AWS EC2 instance types  
  for-example - a.) M6g instances with Graviton processors b.) M6i instances with Xeon Scalable processors  
  both these Graviton & Xeon Scalable processors support always-on `memory encryption`  
  The encryption keys are securely generated within the host system, do not leave the host system,  
  and are destroyed when the host is rebooted or powered down.  

**bash** —  
 a.) The action of caching files when accessing them the first time is called `disk buffering`  
 b.) When a file is read, the data are put into the `page cache`  
 c.) We can use `iostat`, `vmstat`, and `sar` commands to check disk I/O performance.  
 d.) We can also check disk read and write activity by process using the `iotop` command.  
 e.) **page cache**: It is that certain amount of system memory that the kernel reserves for caching the file system disk accesses  
 This is to make overall performance faster,  
 f.) The Linux uses `write-back` approach for caching, and not `write-through`,  
 the former is better in performace but error prone in failover cases.  
 g.) **buffer**: a buffer is an area of memory used to temporarily store data while being moved from one place to another  
 In addition, the `buffer` contains the `metadata of the files` or data which resides under the `page cache`  
 h.) a `cache` is a temporary storage area to store frequently accessed data for rapid access.  
 i.) file /sbin/{`halt`,`poweroff`,`reboot`,`shutdown`} -  
 we can use these system binaries to halt/shutdown/reboot and poweroff the unix machines.  

**vpc-endpoints** —  
 https://docs.aws.amazon.com/vpc/latest/privatelink/vpce-interface.html  
 ![image](https://user-images.githubusercontent.com/26399543/147568840-599a4e76-554b-4407-a2c0-66b196684a40.png)  
 when private DNS (PrivateLink) is turned on:  
 ![image](https://user-images.githubusercontent.com/26399543/147568925-3f709b07-415f-473c-b3d6-735abe8d0ef4.png)  

**S3** —  
 a.) application can achieve at least 3,500 PUT/COPY/POST/DELETE or 5,500 GET/HEAD requests per second per prefix in a S3 bucket  

**EMR** —  
 HDFS-configuration by EMR:  
 ![image](https://user-images.githubusercontent.com/26399543/147821979-e34502b6-dc6d-482a-86e8-63a804af7c19.png)

**Lambda**  
 Lambda functions are protected by AWS Identity and Access Management (IAM) service,  
 which provides both authentication and authorization.  
 **`This is the same mechanism that protects most other AWS services`**.  
 services such as `SNS` and `DynamoDB` are considered secure, even though they don't run inside a VPC  
 
**general-knowledge** —  

 ![image](https://user-images.githubusercontent.com/26399543/147838429-98e09b3f-9047-42dd-8123-7c4d41f47e43.png)
 
 [[readmore]](https://aws.amazon.com/blogs/database/optimizing-costs-in-amazon-rds/) - if you're using a read replica of type db.r4.4xlarge (16 vCPUs) that is 30% utilized,  
 you should consider downsizing to db.r4.2xlarge (8 vCPUs).  
 Now that you have half the number of vCPUs, your CPU utilization is expected to increase to around 60–70%.  
 This leaves a buffer of around 30% for unexpected spikes and future organic increases in traffic.  
