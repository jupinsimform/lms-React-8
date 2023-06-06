# Practical 8

- deploy build on Amazon S3 or any app service
- In this project, AWS S3 and CloudFront Distribution services are utilized to deploy the site. AWS S3 (Simple Storage Service) is used as the storage solution for hosting the website's static files, such as HTML, CSS, JavaScript, and images. CloudFront Distribution is then configured to deliver these files globally, leveraging AWS's Content Delivery Network (CDN) infrastructure.
- This setup provides several benefits, including improved website speed, reduced network latency, enhanced scalability, and the ability to handle high traffic loads. It also allows for easy management of content updates and versioning.
- By combining AWS S3 and CloudFront Distribution, the project achieves a reliable and efficient deployment infrastructure, ensuring a smooth and optimized experience for website users.

# Source Code & 🚀 Live Demonstraion

- Live web-app link : [Site Preview](https://d3tg70co7150ia.cloudfront.net/)

- Source code of above deployed web-app: [source code](https://github.com/jupinsimform/lms-React-5/tree/Practical-5)

# AWS S3

- Amazon Simple Storage Service (S3) is a highly scalable object storage service provided by Amazon Web Services (AWS). It allows you to store and retrieve large amounts of data in a secure and durable manner. Some key features of AWS S3 include:
  > - Object Storage
  > - Scalability
  > - Durability and Availability
  > - Security
  > - Versioning
  > - Lifecycle Management
  > - Data Transfer Options
  > - Integration with Other AWS Services

## AWS S3 Buckets

- An AWS S3 bucket is a container for storing objects in Amazon S3. It is similar to a directory or folder where you can store and organize your files. Each object in S3 is stored in a bucket, and each bucket has a unique name that must be globally unique across all AWS accounts.
- AWS S3 buckets are widely used for a variety of use cases, including storing backups, hosting static websites, serving media files, and powering data lakes and analytics pipelines.

# AWS CloudFront

- AWS CloudFront is a global content delivery network (CDN) service provided by Amazon Web Services (AWS). It accelerates the delivery of your website, application, or content to end-users worldwide by caching and distributing it through a network of edge locations. Here are some key points about AWS CloudFront:
  > - Content Delivery Network
  > - Edge Locations
  > - Distribution
  > - Caching and TTL
  > - Customization
  > - Security
  > - Streaming
  > - Analytics and Reporting

## AWS CloudFront Distributions

- AWS CloudFront Distributions are configurations that define how your content is delivered through the CloudFront CDN.
- By creating and configuring CloudFront Distributions, you can optimize the delivery of your content, improve performance, reduce latency, and enhance the scalability and availability of your applications and websites across the globe.

---

## Prerequisites

- `AWS account` with appropriate permissions to create and manage S3 buckets.

## Deployment Process

## 1. Create S3 bucket

- login into AWS management console.
- Navigate to the S3 service.
- Click on `Create bucket` to create a new bucket.
- Choose unique name for bucket and select region where you want to create it.
- When naming an AWS S3 bucket, it's important to adhere to certain rules and guidelines.
- Here I have created bucket with the name `user-list-react-app`.

  ![create bucket](./assets/create%20bucket.png)

- Edit the Block public access and in that uncheck the `Block all public access`.
- keep rest of the configuration as it is.

  ![public access](./assets/Enable%20public%20access.png)

- After Creating bucket page looks like this

  ![view buckets](./assets/view%20bucket.png)

## 2. Build your React application

- Run npm run build to build the optimized production-ready version of your React app.
- After the build process completes, a build folder will be generated with the bundled files.

## 3. Upload files or folders in bucket

- In the S3 console, go to the `Objects` tab of your bucket.
- Click on the `Upload` button.
- Select the files and folders that you want to upload and click on `upload button`.

  ![upload files & folders](./assets/upload%20files%20%26%20folder.png)

## 4.Create CloudFront distribution

- Navigate to the CloudFront service.
- Click on `Create distributoin` to create a new distribution.
- Choose `Origin domain`(appropriate to your bucket) and `Origin access`.

  ![cloudfront 1](./assets/create%20distribution%201.png)

- Configure control setting.

  ![cloudfront 2](./assets/create%20distribution%202.png)

- set Viewer protocol policy to `Redirect HTTP to HTTPS`.
- keep rest of the configuration as it is & click on `create` button.

  ![cloudfront 3](./assets/create%20distribution%203.png)

- After successfull creation of distribution you can see below page.
- click on `Copy policy` to copy it.

  ![cloudfront 4](./assets/create%20distributoin%204.png)

## 5. Go to S3 bucket permission to update policy

- Navigate to the S3 service.
- Go to your bucket and click on `permission`.
- here in edit bucket policy paste policy that you copied from distribution.
- Click "Save changes" to save the policy.

  ![policy in S3 bucket](./assets/policy%20in%20S3%20bucket.png)

## 6. Add Error Pages in cloudfront(optional)

- Navigate to the CloudFront service.
- Go to your distribution and click on `Error Pages`.
- Add error pages for below 3 error.

  ![error page](./assets/error%20page.png)

## 7. Access your deployed React app

- In cloudfront go to your distribution.
- copy `Distribution domain name` and paste it in any web browser.
- Your React app should now be accessible and deployed on AWS CloudFront.

  ![open site](./assets/open%20site.png)
