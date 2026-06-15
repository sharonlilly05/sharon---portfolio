# Portfolio Website Deployment (Task 2)

This project is a Dockerized Cloud & DevOps portfolio website ready for local testing, GitHub push, and AWS EC2 deployment.

## Project files

- `index.html` — portfolio landing page
- `style.css` — responsive styling and layout
- `Dockerfile` — Docker image build instructions
- `.dockerignore` — files excluded from the Docker build
- `assets/` — optional site assets folder
- `images/` — optional images folder

## Phase 1: Prepare your website

Your project is already ready. The website uses:
- `index.html`
- `style.css`

To match the Task 2 checklist, empty folders `assets/` and `images/` are included.

## Phase 2: Dockerize the website

Create the Docker image inside the project folder:

```bash
docker build -t portfolio-website .
```

Check the image:

```bash
docker images
```

Run the container locally:

```bash
docker run -d -p 8080:80 portfolio-website
```

Open the site in your browser:

```text
http://localhost:8080
```

If the site appears, the Docker part is complete.

## Phase 3: Push code to GitHub

1. Create a repository named `portfolio-website` on GitHub.
2. Run these commands inside the project folder:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/sharonlilly05/portfolio-website.git
git push -u origin main
```

Replace the GitHub URL if your repo has a different name or account.

## Phase 4: AWS EC2 deployment

1. Launch an AWS EC2 instance:
   - Ubuntu
   - t2.micro
   - Allow HTTP (port 80)
   - Allow SSH (port 22)
2. Connect to the instance:

```bash
ssh -i your-key.pem ubuntu@PUBLIC_IP
```

3. Install Docker on EC2:

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

(Optional) Add the `ubuntu` user to the Docker group:

```bash
sudo usermod -aG docker ubuntu
```

4. Clone your GitHub repository on EC2:

```bash
git clone https://github.com/sharonlilly05/portfolio-website.git
cd portfolio-website
```

5. Build and run the Docker image on EC2:

```bash
docker build -t portfolio-website .
docker run -d -p 80:80 portfolio-website
```

6. Open the live site in your browser:

```text
http://PUBLIC_IP
```

## Deliverables

1. `Dockerfile`
2. GitHub repo link: `https://github.com/sharonlilly05/portfolio-website`
3. Screenshot of `docker ps` showing the running container
4. Screenshot of `http://PUBLIC_IP` showing the live website
5. `README.md`

## Commands used

```bash
docker build -t portfolio-website .
docker run -d -p 8080:80 portfolio-website
docker run -d -p 80:80 portfolio-website
```
