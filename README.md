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






    

