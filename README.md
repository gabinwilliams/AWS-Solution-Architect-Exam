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
    

