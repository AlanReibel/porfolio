# DevOps Stack Documentation

## 🐳 Containerization

### Docker
**Nivel:** Avanzado

**Dockerfile Example:**
```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .

EXPOSE 3000
CMD ["node", "server.js"]
```

**Best Practices:**
- Use Alpine images (smaller)
- Multi-stage builds
- Minimize layers
- Don't run as root
- Use .dockerignore

### Docker Compose
```yaml
version: '3.9'
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgresql://...
    depends_on:
      - db
  
  db:
    image: postgres:15
    environment:
      - POSTGRES_PASSWORD=secret
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

## 🔄 CI/CD Pipelines

### GitHub Actions
```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run tests
        run: npm test
      
      - name: Build
        run: npm run build
      
      - name: Deploy
        if: github.ref == 'refs/heads/main'
        run: npm run deploy
```

### GitLab CI
```yaml
stages:
  - test
  - build
  - deploy

test:
  stage: test
  image: node:18
  script:
    - npm ci
    - npm test

build:
  stage: build
  script:
    - npm run build
  artifacts:
    paths:
      - dist/

deploy:
  stage: deploy
  script:
    - npm run deploy
  only:
    - main
```

## 🌐 Web Servers

### nginx
**Nivel:** Avanzado

```nginx
server {
    listen 80;
    server_name example.com;
    
    # SSL redirect
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl;
    server_name example.com;
    
    ssl_certificate /etc/ssl/cert.pem;
    ssl_certificate_key /etc/ssl/key.pem;
    
    # Gzip compression
    gzip on;
    gzip_types text/plain text/css application/json;
    
    # Reverse proxy
    location /api {
        proxy_pass http://app:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
    
    # Static files caching
    location ~* \.(js|css|png|jpg)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }
}
```

### Apache
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    <Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    # URL rewriting
    <IfModule mod_rewrite.c>
        RewriteEngine On
        RewriteRule ^index\.html$ - [L]
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^ index.html [QSA,L]
    </IfModule>
</VirtualHost>
```

## 🐧 Linux & Bash

**Common Commands:**
```bash
# File operations
ls -la                    # List files
mkdir -p dir/nested      # Create nested dirs
cp -r src/ dest/        # Copy recursively
rm -rf dir/             # Remove recursively

# Process management
ps aux | grep process    # List processes
kill -9 PID             # Force kill
jobs                    # Background jobs
fg %1                   # Foreground job

# System info
uname -a                # System info
df -h                   # Disk usage
htop                    # Process monitor
```

**Useful Scripts:**
```bash
#!/bin/bash

# Backup script
BACKUP_DIR="/backups"
SOURCE_DIR="/data"
DATE=$(date +%Y%m%d)

tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" "$SOURCE_DIR"
find "$BACKUP_DIR" -mtime +30 -delete  # Keep last 30 days
```

## 📊 Monitoring & Logging

**Monitoring Stack:**
- Prometheus (metrics)
- Grafana (visualization)
- ELK Stack (logging)
- Sentry (error tracking)

**Key Metrics:**
```
- CPU usage
- Memory usage
- Disk usage
- Request latency
- Error rates
- Throughput
```

## 🔒 Security Hardening

**Checklist:**
```bash
# SSH hardening
- [ ] Disable root login
- [ ] Use SSH keys only
- [ ] Change default port 22
- [ ] Fail2ban enabled

# Firewall
- [ ] ufw/iptables configured
- [ ] Only necessary ports open
- [ ] Rate limiting enabled

# Updates
- [ ] Regular OS updates
- [ ] Security patches
- [ ] Container scanning
```

## 🚀 Git Workflows

**Branch Strategy (Git Flow):**
```
main (production)
├── release/1.0
└── develop
    ├── feature/new-api
    ├── feature/optimization
    └── bugfix/issue-123
```

**Commit Convention:**
```
feat(user): add authentication
fix(api): handle null responses
docs(readme): update setup guide
style(css): format code
refactor(db): optimize queries
test(auth): add login test
chore(deps): update dependencies
```

## 🔧 Infrastructure as Code

**Terraform Example:**
```hcl
resource "aws_instance" "app" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  
  tags = {
    Name = "app-server"
  }
}

resource "aws_rds_instance" "db" {
  engine       = "postgres"
  instance_class = "db.t3.micro"
  allocated_storage = 20
}
```

---

**Last Updated:** February 13, 2025
