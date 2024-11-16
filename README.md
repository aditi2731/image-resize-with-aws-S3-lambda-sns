# image-resize-with-aws-S3-lambda-sns

## STEPS TO DO IMAGE RESIZE WITH AWS S3 , AWS LAMBDA and AWS SNS
*This project focuses on building an automated system for image processing and management in AWS. The goal is to streamline the handling of images by automatically resizing them and transferring them to a designated storage location while keeping owner informed via notifications on their emails. Key AWS services used in this project are Lambda, S3, Simple Notification Service.*

# Creating Source and destination S3 buckets:

1. Navigate to S3 console, click on create bucket.
2. Name the Bucket and leave the rest of the settings as default and click on "Create Bucket". This is the source bucket created.
3. Repeat the 2 step to create the destination bucket.

# Creating the SNS Notification:

1. Navigate to SNS console.

2. Click on "Create topic" and select type standard and name it keep the other settings as it is and click on "Create topic".
3. Click on "Create Subscription" and click on select protocol and choose email , and put your email address on endpoint and create subscription.
4. After this email will be delivered on email for confirmation.

# Creating Lambda Function

1. Navigate to Lambda console.
2. Create the lambda function keeping author from scratch and runtime (Python 3.9).
3. Now put the code in image-resize.py in editor and deploy it.
4. Navigate to the IAM console and create policies for S3 grant all permissions to it , SNS grant all permissions to it , Lambda grant only read permission to it.
5. Go back to lambda console and go to configuration > go to permissions > role name > add permissions > search the policy you have created and add permissions.
6. Now we have to trigger the lambda function. Configuration > Triggers > Add Trigger > select S3 > choose bucket > Add.
7. Now go to scroll section and scroll down to layers. Add a Layer > Specify an ARN (arn:aws:lambda:eu-north-1:770693421928:layer:Klayers-p39-pillow:1) use the present region >Verify > Add.
8. Test the code.
9. It will show some error because nothing is uploaded in S3.

# Uploading image to S3

1. Upload the image to Source S3 bucket.
2. We can see that automatically a new folder is created for us and inside this folder we can se resized image.
3. We can see that image has been resized and uploaded in our destination bucket.
4. The email will be recieved that image has been resized and uploaded to destination bucket.


   
   ![Screenshot 2024-11-16 223704](https://github.com/user-attachments/assets/6f730cf2-affa-4053-9a0e-bc6dc06993a7)
