# Amazon S3 - Static Website Hosting with Custom Domain and TLS
Made use of AWS services like  S3, Certificate Manager, Cloud Front, Route53. Also used Hostinger.com to purchase the domain
## Agenda:  
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/66f8fd9a-4bd8-4805-8e60-7f8580b56119">

1.	We are creating a static website that is fully functional with global reach. The website can be your portfolio or any other website. The choice is yours. 
2.	We must use **all the above AWS services** as shown in the diagram for this project. For the Domain Names, we are using hostinger.com. 

Pre-requisites:
1.	AWS Account is Required. If you have one already, use it. Otherwise, create an account with AWS [https://portal.aws.amazon.com/billing/signup#/start/email](https://portal.aws.amazon.com/billing/signup#/start/email)
2.	Purchase a domain from [hostinger.com](https://www.hostinger.com/) as they offer affordable domains when you compare with AWS domain name services.
   
From AWS,

<img width="456" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/4a55ce4c-5eff-46f9-a6fb-f3c2691f9bd7">

From Hostinger,

<img width="457" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/38de1179-40fc-4248-a475-e6a6cb6a5a7f">


3.	The domain name can be your net-id or full name.
   
   a) On the hostinger.com homepage, choose **Domains** from the menu options.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/b304a4c8-21b6-47c9-a5de-0b8fa6f88a32">

   b) On the search bar, type your full name and search for the available domains. You can choose the cheapest option available. I would go with something that is cheaper and meaningful.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/b49b7a5c-995e-44b8-9119-3102260a547d">

   c) Choose one and **add to cart**. Verify that the period chosen is 1 year. Create the Hostinger account. If we use the same email which was used to create AWS account, we will have an additional option to do the email validation for the AWS Certificate Manager. Make the payment and That’s it. You owned a domain name now.

## Steps:

### 1.Static Website.

   a) Create an S3 bucket with the domain name. Ex: **venkatagirisasanapuri.cloud**. Leave the other options to the default.
   
   b) Enable **Static Website Hosting**. Scroll down to the bottom of the **Properties** tab and enable it. Make sure to change the name of the **Index document**. (Ex: index.html)
   
   c) Add the bucket policy and uncheck the **Block Public access** option. We will have to change the bucket policy once the Cloudfront distribution is created to make sure the website is accessible only through domain name.

<img width="294" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/2e0aaf0f-26fb-43b5-9a41-dd4b9196be36">
      
   Expectation: When I hit the static URL, I can see a webpage in the browser as shown below.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/f7bcafa4-b56a-4772-9093-826085268e13">

### 2.Create a certificate from the AWS Certificate Manager.

   a) Request a certificate from the AWS Certificate Manager with the domain name.
   
   b) Choose DNS validation method as it is a flexible option to update the CNAME. Leave rest of the options to default and Request for the certificate.
   
   c) Once the certificate is created, validation needs to be done to prove the ownership of the domain name. We will do it in the upcoming steps.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/d142c19d-8beb-4ebd-b036-43b114030684">



### 3.Create a hosted zone in the Route 53.

   a) Enter the Domain name (venkatagirisasanapuri.cloud) and Create the hosted zone. Once the zone is created, go the **Certificate Manager**. We have to copy the CNAME name and CNAME value by selecting **Create records in Route 53 option**. 
   
   b) We will have to update the Hosted zone by adding the A record type, once the Cloudfront Distribution is created.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/6710823c-0513-4d5d-9a60-1a3aef568ce1">

### 4.Create the Cloudfront Distribution.

   a) Select the S3 bucket, and in the Origin access option, select Origin access control settings option which is the recommended one and Click **Create control setting** option. 
      
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/4b8857fc-08dd-4109-9c4d-95ed8ac194cb">

   b) By selecting the control settings option, we are updating the policy in the s3 bucket policy.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/af59d8e3-f900-4165-b8ac-379a09ffa6e4">

   c) Change the Viewer protocol policy to **Redirect HTTP to HTTPS**.
   
   d) Under cache policy, choose Caching Optimized.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/36f8eb64-6b02-4e64-9c47-ea1bf274960e">

   e) Do not enable security protections under WAF.
   
   f) Choose Custom SSL certificate that was created earlier in the Certificate Manager option.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/618333f3-f6e5-4015-a048-2e6b89f313b2">

   g) Under **Default root object**, add index.html file.
   
   h) Scroll down and create the distribution. Once the distribution is created, Copy the policy and update the s3 bucket policy **yet again**.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/5cda3b76-6af3-4fd6-8d8b-283ddb2b4297">

   i) Screenshot of the updated bucket policy.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/bfff629e-3369-4fd5-992d-7a4741eea661">

   j) Once the bucket policy is updated, see that the website is accessible with the Cloudfront distribution.

<img width="468" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/9c02751f-a93e-449b-931b-318e0931b0ae">

### 5.Update the Route 53 records.

   a) Now, we have to create a record in the hosted zone created earlier. Select the **Record type**, A and turn on the **Alias** option. Under Route traffic, we have to select Cloudfront from the first drop down and then select the Cloudfront distribution.

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/0add1022-29ed-4fe0-8251-4af71cdcb218">

## Final Output:

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/27d791c3-94d5-4d7e-8f63-26e86e55ad2e">
