🖼️ AWS Image Analyzer with Rekognition

A serverless project that analyzes images using Amazon Rekognition and displays the results on a static website. Built to practice AWS cloud services, serverless pipelines, and computer vision.

⚙️ Architecture

User (Browser) 
   → Amazon CloudFront (OAC) 
      → S3 (Website Bucket: index.html, script.js, style.css)

User Upload (Image) 
   → S3 (Data Bucket: uploads/) 
      → S3 Event Trigger 
         → AWS Lambda (Python) 
            → Amazon Rekognition (Label Detection) 
               → S3 (Data Bucket: results/ + latest.json) 
                  → Served back via CloudFront 
                     → User sees Image + Labels

Services Used:

Amazon S3 → store website, uploads, and JSON results

AWS Lambda → triggered on image upload, calls Rekognition, writes results

Amazon Rekognition → label/object detection

Amazon CloudFront → global CDN + HTTPS for static website

IAM / OAC → secure access between CloudFront and private S3 buckets

Flow:

Upload an image → stored in uploads/ folder of the data bucket.

S3 event triggers Lambda.

Lambda calls Rekognition → saves results as JSON in results/.

Lambda also updates latest.json → always points to most recent file.

Static website fetches latest.json and displays image + labels.

📂 Bucket Setup

Website Bucket (image-analyzer-website):

index.html, style.css, script.js

Data Bucket (vid-image-scan):

/uploads/ → uploaded images

/results/ → Rekognition output JSON

CloudFront Behaviors:

* → website bucket

/uploads/* → data bucket

/results/* → data bucket


🔐 Security

Buckets are private (no public access).

Access controlled with CloudFront Origin Access Control (OAC).


🎯 Key Learnings

Connecting S3 + Lambda + Rekognition into a serverless workflow.

Using CloudFront behaviors to serve static website + dynamic data.

Enforcing private access with OAC instead of public buckets.

📌 Links
🔗 youtube Demo :https://youtu.be/GPMW1rLMY1U
🔗 web Demo: d2dndqfio8c53w.cloudfront.net
