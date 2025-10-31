# Daily-learning-progress
Routine task learning progress report


what is cloud?
Cloud computing means that your data and applications are stored on servers on the internet.

aws sts get-caller-identity  # Our identity check
  aws ec2 describe-regions     # All regions ki list
  aws s3 ls                    # S3 buckets ki list (simple storage service)


WEEK 1 - AWS LEARNING NOTES
============================

📝 RESEARCH NOTES (Day 1)
=========================

IAM (Identity & Access Management):
- What is IAM and why do we use it?
  its a framework of policies that can be only accesible for authorized person 
  those who wants to use the organizations services and resources and 
  we use it for prevent the data breaches

- Difference between Users, Groups, Roles, and Policies:
  
  Users - an individual identity or a person who have intraction with aws services 
  and have long term credentials and assinged permissions individually or via groups
  
  Groups - Group is a collection of IAM users with shared permissions
  to simplifying Management scale instead of assingning permissions individually
  user can belong multiple Groups. 
  a Group is assinged policies and all members can inherit those permissions

  Roles - IAM Roles is a set of permissions 
  that can be temporarily assumed by trusted entities 
  and not have long term credentials

  policies - IAM policies is a jSON Document that defines permissions 
  policies are define that what kind action can be allowed or denied
  policies can be attachced to users,groups and Roles.

- What are Access Keys and Secret Keys?
  Access key - its an unique key for identify the user

  Secret key - this is confidential key 
  that is used with conjuction or 
  we can say use in parallel with Access key to sign in securely
  it should be kep secret not shared publicly

  S3 (Simple Storage Service):
- What is object storage?
  object Storage it is a modern data storage technology it is desinged for handling the 
  unstructured data such as video,images,emails and sensor data.

- What is the purpose of buckets?
  Bucket is a cloud storage container that hold our data and it must be stored within 
  a buckets. buckets help us to organize the data and control Access to it.
