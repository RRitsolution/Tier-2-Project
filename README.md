Tier-2 Project Microservices Base (Including Docker Network Concept)

Project Overview:-

Tier-1: Frontend / Presentation Layer – User Interface Web server serves a static HTML file to the user.

API: Middle layer between Frontend & Backend (to enable connection between Frontend and Backend).

Tier-2: Backend / Main Application logic – responds to user via API middle layer on presentation layer.

Infrastructure Used: Microservices-based architecture for this project.

👉 1 Container for Frontend, 1 Container for Backend & 1 Container for API

Techs Used: Nginx, Python, Flask
Frontend-Nginx-based container(default.conf-Nginx configuration file & index.html in frontend directory)
API-Nginx-based container(default.conf-Nginx configuration file & index.html in backend directory)
Backend-Python base container with Flask web server framework(app.py main application code, requirements.txt for dependencies & Dockerfile for build image in backend directory)

Application Flow:

 User (Browser) → Frontend Container → API Container → Backend Container

Networking Concept (in simple words):

By default, when Docker is installed and started, a network called docker0 bridge network is created with a pool of IPs (subnet). This allows communication between containers and with the host.

But what if you want isolation between containers (so they don’t talk to each other on the same Docker engine/host)?

 ✅ This can be achieved by creating custom networks and attaching containers to them while creating.

Example:

Container-A & Container-B are both attached to the default docker0; they can communicate.

If Container-A is on network A and Container-B is on network B, then they cannot communicate (different networks/subnets).

Final Concept Applied:

Front-end and back-end containers are placed in different networks.

Backend is isolated (secure, not directly exposed to the public or the frontend).

To enable communication, the API container is attached to both networks (network A & network B).

So, Frontend communicates with Backend only via the API container.



I have used the Docker Compose concept for this microservice-based application .


Commands to run this application:-

docker-compose up -d --build




