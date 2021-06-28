# AWS-Solutions-Architect-Exam
This repo will be used for note taking to prep for the certification exam.

# Region, Availability Zone (AZ), and Edge Location

- Region: A physical location in the world which consists of two or more AZ's.

- Availability Zone: An AZ is one or more discrete data centers, where redundant power, networking and connectivity, is housed in separate facilities.

- Edge Location:  Endpoints for AWS which are used for caching content.  Typically consists of CloudFront, Amazong's Content Delivery Network (CDN).

# Quiz 1

1. What does VPC stand for?  
  - Virtual Private Cloud.
2. An AWS VPC is a component of which group of AWS services?
  - Networking Services.
3. What does an AWS Region consist of?
  - A distinct location within a geographic area designed to provide high availability to a specific geography.
4. Which statement best describes Availability Zones?
  - Distinct locations from within an AWS region that are engineered to be isolated from failures.
5. What is an AWS region?
  - A region is a geographical area divided into Availability Zones. Each region contains at least two Availability Zones.
6. The number of Edge Locations is greater than the number of Availability Zones, which is greater than the number of Regions.
7. In which of the following is CloudFront content cached?
  - Edge Location.

  # Identity Access Management (IAM)
  1. IAM allows you to manage users and their level of access to the AWS console.

  MAIN FEATURES:
    - Centralized control of aws account
    - Shared access to account
    - Granular permissions
    - Identity federation (login/sign up with google, facebook ect)
    - Multi-factor Auth
    - Provide temp access for users/devices
    - Set up password rotation policy
    - Supports PCI DSS compliance (credit card ect)

  MAIN GROUPS:
    1. USERS - individual
    2. GROUPS - all users of group inherit group access rules
    3. POLICIES - JSON object made up of rules and access for groups, roles ect
    4. ROLES - created and then assigned to give access

  FACTS:
    - IMA is universal.  Doesn't require region lock and is global.
    - Root account is first account created when setting up AWS.  This account has complete admin access.
    - New users have NO permissions by DEFAULT
    - New users are assigned an access key ID and secret access key during account creation.
        - cannot be used to access the console.  Only access to AWS via terminal or APIs.
    - Access Key ID and Secret Access Key may only be used once and will need to be regenerated once used.
    - ALWAYS setup Multi-access Auth on root account.
    - Create and customize your own password policies.

## Chapter 4

  # BILLING ALARM

    1. Navigate to all services, CLOUD WATCH.
    2. Create a SNS (Simple Notification Service) email notification to warn user if bill crosses certain threshold.

  # S3
    - A safe place to store your files.
    - Object-based... allows you to upload files.
        - file size anywhere from 0 Bytes to 5 TB.
    - Unlimited storage
    - Files are stored in buckets (folder)
    1. S3 is universal name space.... meaning each bucket name must be unique globally
      - Bucket names are URL based so that is why it must be unique.
    2. When you upload a file to S3 you will receive a (HTTP 200 CODE) is the file upload was successful.
    3. S3 OBJECT:
      - Key (name)
      - Value (sequence of bytes)
      - Version ID (important for versioning)
      - MetaData (data about data you are storing)
      - Sub-resources
          - Access Control Lists
          - Torrent
    4. S3 Data Consistency:
      1. (Read after Writes consistency) for PUTS of new objects
      2. (Eventual consistency) for overwrite PUTS and DELETES.... meaning slight delay with overwriting.
      
    5. S3 Guarantees from Amazon:
      1. Built for 99.99% of S3 platform
      2. Amazon guarantees 99.9% availability
      3. Amazon guarantees 99.999999999% durability for S3 information. (11 x 9s) meaning it won't be lost.

    6. S3 Features:
      1. Tiered Storage options

          1. (S3 Standard)
            - 99.99% availability
            - 99.999999999% durability stored redundantly across multiple facilities on multiple devices and is designed to sustain a loss of 2 facilities concurrently.
            - Data in Milliseconds

          2. (S3 IA or infrequently accessed)
            - Data that is accessed less frequently but needs rapid access when used.
            - Lower fee than S3 Standard
            - Induces a retrieval fee
            - Data in Milliseconds

          3. (S3 One Zone IA)
            - Data that is accessed less frequently but needs rapid access when used.
            - Lower Cost than IA
            - Doesn't require multi-availability-zone data resilience
            - Data in Milliseconds

          4. (S3 Intelligent Tiering)
            - Uses machine learning to optimize costs by moving data to the most cost-effective tier option without compromising performance or operational overhead.
            - Data in Milliseconds

          5. (S3 Glacier)
            - Secure, Durable, low-cost storage
            - No limit on amount
            - prices are competitive or cheaper than on-site solutions
            - retrieval times configurable from minutes to hours
            - Data in Min to hours

          6. (S3 Glacier Deep Archive)
            - Lowest cost option
            - 12hr retrieval time is acceptable
            - Data in hrs

        1. Pricing in S3
            - Storage amount
            - Requests
            - Storage management pricing.... which tier you have selected
            - Data Transfer
            - Transfer acceleration (this uses cloudFront/edge locations)
            - Cross region replication


      2. Life Cycle Management
      3. Versioning
      4. Encryption
      5. MFA to Delete objects
      6. Secure your data using (Access Control Lists) and (Bucket Policy)

  ## S3 EXAM RECAP

    1. S3 is object based and allows for file upload.
    2. Files allowed are 0 bytes - 5tb
    3. Unlimited storage
    4. Files are stored in buckets
    5. S3 Bucket is a universal name-space.... means name must be unique globally.
    6. Bucket name is URL based
    7. Not suitable to install an OS on because its object based (block-based needed for that)
    8. On successful upload, you will get an HTTP 200 status code.
    9. You can turn on MFA Delete (file/object protection)
    10. S3 OBJECT:
      - Key (name)
      - Value (sequence of bytes)
      - Version ID (important for versioning)
      - MetaData (data about data you are storing)
      - Sub-resources
          - Access Control Lists
          - Torrent
    11.  **** READ THROUGH S3 FAQs before taking the exam!****

  ## S3 Bucket Recap
    1. Buckets are global, but when you create one, you assign it a region of choice
    2. You can replicate buckets using Cross Region Replication
    3. Restricting Bucket Access
        - Bucket Policy - applied across entire bucket
        - Object Policy - applied only to that object
        - IAM Policy to users and groups - applies to users and groups

# S3 Storage Costs
  1. S3 Standard:
    - 50TB a month @ 0.023 per GB
    - 450TB a month @ 0.022 per GB
    - 500TB a month @ 0.021 per GB

  2. S3 Intelligent Tiering - Automatic cost saving with moving around files on access frequency
    - 50TB a month @ 0.023 per GB
    - 450TB a month @ 0.022 per GB
    - 500TB a month @ 0.021 per GB
    - IA all storage @ 0.0125 per GB
    - Monitoring and Automation all storage @ 0.0025 per 1,000 objects

  3. S3 Standard IA - for long lived but IA data that needs millisecond access
    - All storage / month @ 0.0125 per GB

  4. S3 One Zone IA - for re-creatable IA data that needs millisecond access
    - All storage / month @ 0.01 per GB

  5. S3 Glacier - long-term backups retrieval from 1 min to 12hrs
    - All storage / month @ 0.004 per GB

  6. S3 Glacier Deep Archive - long-term backups accessed once or twice a year. 12hr retrieval
    - All storage / month @ 0.00099 per GB

# S3 Security and Encryption

  1.  By DEFAULT all buckets are created (PRIVATE)
    - You can setup access control for buckets through:
        - Bucket policies
        - Access Control Lists
  2. Buckets can be configured to use access logs which logs all requests made to that bucket
    - The logs can be sent to another bucket or even another bucket for a different account

  ## Encryption

    1. Encryption in transit or (HTTPS)
      - SSL/TLS

    2. Encryption at REST (Server Side)
      - S3 managed keys (SSE S3) - server-side-encryption
      - AWS Key Management service - keys managed together (SSE KMS)
      - Server-side Encryption with customer provided keys (SSE-C)

    3. Encryption at REST (Client Side)
      - Client encrypts files before uploading to S3

# S3 Versioning
  1. Stores all versions of an object - including all writes and even if you delete the obj
  2. Great backup tool
  3. Once enabled VERSIONING CANNOT BE DISABLED, only SUSPENDED
  4. Integrates with lifeCycle rules
  5. Versioning MFA Delete functionality - used to provide an extra layer of security

# Life Cycle Management
  1. Allows you to automate file movement between the storage tiers
  2. Can be used in conjunction with versioning
  
# S3 Object Lock

  1. Write once, read many (WORM).  Helps obj from getting deleted or modified for a fixed amount of time or indefinitely.

  2. Used to meet regulatory requirements that require WORM storage or add an extra layer of protect for modification or deletion 

  ## Object Lock MODES

    1. Governance mode
      - Users can't overwrite, delete an obj version, or alter lock settings unless special permissions are given

    2. Compliance mode
      - A protected object version can't be overwritten or deleted by any user.
      - Even the root user can't alter or delete obj until retention is over.

      3. Retention Period
        - Protects and obj version for a fixed amount of time
        - Once retention expires, obj may be deleted or overwritten
        - Timestamp living in the obj metadata of when retention expires
      4. Legal hold
        - Prevents obj version from being deleted or overwritten
        - Doesn't expire.  Must be removed.
        - Can be placed or removed freely by users with permission "S3: PutObjectLegalHold"

    3. Glacier vault lock
      - vault lock policy
      - enable WORM
      - Lock policy from edits
      - Once locked, policy can no longer be changed

    ## LOCK MODE EXAM TIPS

      1. S3 object lock 
        - uses (WORM), Write once, ready many
        - Obj lock can be applied to individual objects or applied to the entire bucket
        - Two modes: Governance and compliance

# S3 Performance 

  1. Continue today




    

