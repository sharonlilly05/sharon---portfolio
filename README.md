# Static Portfolio Website

This repository contains a polished single-page portfolio template for AWS S3 static hosting and CloudFront HTTPS delivery.

## Files

- `index.html` — portfolio landing page
- `style.css` — responsive styling and layout

## Local setup

1. Open the project folder in a code editor.
2. Preview `index.html` in a browser.

## Deployment steps

1. Initialize the repository and commit the project:
   ```bash
   git init
   git add index.html style.css README.md
   git commit -m "Add portfolio website"
   ```
2. Create an S3 bucket, for example:
   ```bash
   aws s3 mb s3://yourname-portfolio
   ```
3. Enable static website hosting in the S3 bucket and configure the index document to `index.html`.
4. Update public access settings to allow website hosting and add a bucket policy for `s3:GetObject`.
5. Upload the files to S3:
   ```bash
   aws s3 sync . s3://yourname-portfolio --acl public-read
   ```
6. Test the S3 website endpoint in a browser.
7. Create a CloudFront distribution using the S3 bucket as origin.
   - Set Viewer Protocol Policy to `Redirect HTTP to HTTPS`
   - Choose a minimum TLS version such as `TLSv1.2`
8. Use the CloudFront domain as your hosted URL.

## Notes

- Replace `Sharon` and `sharon@example.com` with your real name and email address if needed.
- If you want to map a custom domain, configure DNS in Route 53 or your domain registrar to point to the CloudFront distribution.

## Optional

- Add `assets/` with images if needed.
- Capture screenshots of the CloudFront distribution and S3 bucket policy for task submission.
- Record a short screen video showing the live site.
