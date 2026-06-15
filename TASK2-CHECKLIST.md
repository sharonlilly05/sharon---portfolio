# Task 2 Checklist

## Phase 1: Prepare website
- Ensure the project contains:
  - `index.html`
  - `style.css`
  - `Dockerfile`
  - `.dockerignore`
  - optional `assets/` and `images/` folders

## Phase 2: Dockerize locally
1. Build Docker image:
   ```bash
   docker build -t portfolio-website .
   ```
2. Verify Docker image exists:
   ```bash
   docker images | grep portfolio-website
   ```
3. Run the container locally:
   ```bash
   docker run -d -p 8080:80 portfolio-website
   ```
4. Open in browser:
   ```text
   http://localhost:8080
   ```
5. Confirm site loads successfully.

## Phase 3: Push code to GitHub
1. Initialize Git repository if not already initialized:
   ```bash
   git init
   ```
2. Add files:
   ```bash
   git add .
   ```
3. Commit:
   ```bash
   git commit -m "Initial commit"
   ```
4. Create `main` branch and add remote:
   ```bash
   git branch -M main
   git remote add origin https://github.com/sharonlilly05/portfolio-website.git
   ```
5. Push to GitHub:
   ```bash
   git push -u origin main
   ```

## Phase 4: AWS EC2 deployment
1. Launch EC2 instance:
   - Ubuntu
   - t2.micro
   - allow HTTP (80) and SSH (22)
2. Connect via SSH:
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
4. (Optional) Add user to Docker group:
   ```bash
   sudo usermod -aG docker ubuntu
   ```
   Then logout and log back in.
5. Clone your GitHub repo:
   ```bash
   git clone https://github.com/sharonlilly05/portfolio-website.git
   cd portfolio-website
   ```
6. Build Docker image on EC2:
   ```bash
   docker build -t portfolio-website .
   ```
7. Run container on port 80:
   ```bash
   docker run -d -p 80:80 portfolio-website
   ```
8. Open the live website:
   ```text
   http://PUBLIC_IP
   ```

## Deliverables
- `Dockerfile`
- GitHub repo link: `https://github.com/sharonlilly05/portfolio-website`
- Screenshot of `docker ps` showing the running container
- Screenshot of the live site at `http://PUBLIC_IP`
- `README.md` detailing the deployment steps

## Notes
- Replace `PUBLIC_IP` with the actual EC2 instance public IP.
- If `docker run` fails because port 80 is in use, stop the conflicting service or choose a different port.
- Keep screenshots for `docker build`, `docker run`, `docker ps`, EC2 instance details, and live website.
