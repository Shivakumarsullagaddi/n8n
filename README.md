# n8n Docker Setup with ngrok

This repository helps you quickly run **n8n using Docker** and expose it to the internet using **ngrok**.

n8n is an open-source workflow automation tool that allows you to connect APIs, automate tasks, and build integrations.  
ngrok creates a secure tunnel that exposes your local server to the internet through a public URL. :contentReference[oaicite:0]{index=0}

---

# Project Structure

```
n8n-setup/
│
├── Dockerfile
├── docker-compose.yml
├── .env
└── README.md
```

---

# Prerequisites

Before running this project, install the following:

### 1️⃣ Install Docker Desktop

Download and install Docker Desktop.

https://www.docker.com/products/docker-desktop/

Verify installation:

```bash
docker --version
```

---

### 2️⃣ Install ngrok

Download ngrok from:

https://ngrok.com/download

Verify installation:

```bash
ngrok --version
```

---

### 3️⃣ Create ngrok Account

Create a free account:

```
https://dashboard.ngrok.com
```

After login, copy your **Auth Token**.

Authenticate ngrok with your account:

```bash
ngrok config add-authtoken YOUR_AUTHTOKEN
```

This command saves your token in the local configuration file. :contentReference[oaicite:1]{index=1}

---

# Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

```bash
cd n8n-setup
```

---

# Environment Variables

Inside the project there is a file:

```
.env
```

Example configuration:

```env
DOMAIN_NAME=your-ngrok-domain.ngrok-free.dev
GENERIC_TIMEZONE=Europe/Berlin
SSL_EMAIL=user@example.com
```

⚠️ Important:  
Do **NOT use the example domain above**.

Each user must set their **own ngrok domain**.

Example:

```
DOMAIN_NAME=abcd1234.ngrok-free.dev
```

---

## Explanation

### DOMAIN_NAME

Your public domain provided by ngrok.

Example ngrok URL:

```
https://abcd1234.ngrok-free.dev
```

Set the domain like this:

```
DOMAIN_NAME=abcd1234.ngrok-free.dev
```

---

### GENERIC_TIMEZONE

Timezone used by n8n workflows.

Examples:

```
GENERIC_TIMEZONE=Asia/Kolkata
GENERIC_TIMEZONE=Europe/Berlin
GENERIC_TIMEZONE=America/New_York
```

---

### SSL_EMAIL

Email used for SSL related configuration.

Example:

```
SSL_EMAIL=your_email@gmail.com
```

---

# Running the Project

### Step 1 — Start ngrok

Expose the local n8n server to the internet.

```bash
ngrok http 5679
```

ngrok will generate a public URL.

Example:

```
Forwarding https://abcd1234.ngrok-free.dev -> http://localhost:5679
```

Copy the domain and place it in `.env`.

---

### Step 2 — Start Docker Containers

Run the following command:

```bash
docker compose up -d
```

This will start n8n in the background.

---

### Step 3 — Stop Containers

```bash
docker compose down
```

---

# Access n8n

Local access:

```
http://localhost:5679
```

Public access:

```
https://your-ngrok-domain.ngrok-free.dev
```

---

# Useful Commands

Start containers:

```bash
docker compose up -d
```

Stop containers:

```bash
docker compose down
```

Run ngrok:

```bash
ngrok http 5679
```

---

# How It Works

```
User → ngrok Public URL → Localhost:5679 → Docker Container → n8n
```

ngrok creates a secure tunnel that forwards internet traffic to your local machine. :contentReference[oaicite:2]{index=2}

---

# Common Issues

### ngrok command not found

Ensure ngrok is installed and added to PATH.

---

### Docker not starting

Restart Docker Desktop.

---

### Port already in use

Change the port inside `docker-compose.yml`.

Example:

```
5679:5679
```

---

# Use Cases

This setup is useful for:

- Webhook testing
- API integrations
- Workflow automation
- Development environments

Running n8n locally with Docker and exposing it through ngrok is a common approach for testing integrations and webhooks. :contentReference[oaicite:3]{index=3}

---

# License

MIT License

---

# Contributing

Pull requests are welcome.

If you find issues or improvements, feel free to create an issue or submit a PR.
