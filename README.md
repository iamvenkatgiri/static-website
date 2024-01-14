# Amazon S3 - Static Website Hosting with Custom Domain and TLS
Made use of AWS services like  S3, Certificate Manager, Cloud Front, Route53. Also used Hostinger.com to purchase the domain
## Agenda:  
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/66f8fd9a-4bd8-4805-8e60-7f8580b56119">

1.	We are creating a static website that is fully functional with global reach. The website can be your portfolio or any other website. The choice is yours. 
2.	We must use all the above AWS services as shown in the diagram for this project. For the Domain Names, we are using hostinger.com. 

Pre-requisites:
1)	AWS Account is Required. If you have one already, use it. Otherwise, create an account with AWS [https://portal.aws.amazon.com/billing/signup#/start/email](https://portal.aws.amazon.com/billing/signup#/start/email)
2)	Purchase a domain from hostinger.com as they offer affordable domains when you compare with AWS domain name services.
   
From AWS,

<img width="456" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/4a55ce4c-5eff-46f9-a6fb-f3c2691f9bd7">


From Hostinger,

<img width="457" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/38de1179-40fc-4248-a475-e6a6cb6a5a7f">


3)	The domain name can be your net-id or full name.
   
   a)On the hostinger.com homepage, choose Domains from the menu options.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/b304a4c8-21b6-47c9-a5de-0b8fa6f88a32">

   b)On the search bar, type your full name and search for the available domains. You can choose the cheapest option available. I would go with something that is cheaper and meaningful.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/b49b7a5c-995e-44b8-9119-3102260a547d">

   c)Choose one and add to cart. Verify that the period chosen is 1 year. Create the Hostinger account. If we use the same email which was used to create AWS account, we will have an additional option to do the email validation for the AWS Certificate Manager. Make the payment and That’s it. You owned a domain name now.

## Steps:

### 1.Static Website.
   a)Create a static website using s3. 
   b)The name of the bucket can be domain name that you bought from hostinger. For Ex: The bucket name is: venkatgirisasanapuri.cloud
   Expectation: When I hit the static URL, I can see a webpage in the browser as shown below.
   
<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/f7bcafa4-b56a-4772-9093-826085268e13">

### 2.Create a certificate from the Amazon Certificate Manager for the DNS purchased at hostinger website.
### 3.Create a Cloudfront Distribution.
### 4.Create a hosted zone in the Route 53 and do the necessary steps to accomplish the project.

## Final Output:

<img width="470" alt="image" src="https://github.com/iamvenkatgiri/static-website/assets/156535839/27d791c3-94d5-4d7e-8f63-26e86e55ad2e">
