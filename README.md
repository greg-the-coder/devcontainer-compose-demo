# Coder AWS Linux EC2 Container Template Demo

This repository demonstrates a complete development environment setup using [Coder](https://coder.com) with AWS EC2 and Development Containers (devcontainers). It showcases how to create consistent, reproducible development environments that can be instantly provisioned in the cloud.

## 🚀 What is This?

This example implements the [AWS Linux EC2 Container template](https://github.com/greg-the-coder/partner-demo-gitops/tree/main/templates/aws-linux-ec2-container) from Coder, providing:

- **Cloud-based development environment** running on AWS EC2
- **Containerized workspace** with Python 3.12 and PostgreSQL
- **Pre-configured tooling** including Poetry, Zsh, and VS Code extensions
- **Database connectivity** with a sample Python application

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────┐
│ AWS EC2 Instance (Coder Workspace)      │
│ ┌─────────────────────────────────────┐ │
│ │ Development Container               │ │
│ │ ├── Python 3.12                    │ │
│ │ ├── Poetry (dependency management)  │ │
│ │ ├── Zsh with customizations        │ │
│ │ └── VS Code Server                 │ │
│ └─────────────────────────────────────┘ │
│ ┌─────────────────────────────────────┐ │
│ │ PostgreSQL Container                │ │
│ │ ├── Database: postgres             │ │
│ │ ├── User: postgres                 │ │
│ │ └── Port: 5432                     │ │
│ └─────────────────────────────────────┘ │
└─────────────────────────────────────────┘
```

## 📁 Project Structure

```
.
├── .devcontainer/           # Development container configuration
│   ├── devcontainer.json   # VS Code devcontainer settings
│   ├── docker-compose.yml  # Multi-container setup
│   └── Dockerfile          # Custom Python environment
├── main.py                 # Sample Python application
├── pyproject.toml          # Poetry project configuration
├── poetry.lock             # Locked dependencies
└── .gitignore             # Git ignore patterns
```

## 🛠️ Development Environment Features

### Container Configuration

The development environment includes:

- **Base Image**: Python 3.12 on Debian Bullseye
- **Shell**: Zsh with oh-my-zsh and custom themes
- **Package Manager**: Poetry for Python dependency management
- **Database**: PostgreSQL 16 with persistent storage
- **Docker Support**: Docker-outside-of-Docker for container operations

### VS Code Integration

Pre-configured extensions and settings:
- Python language support with Pylance
- Zsh terminal with Hack Nerd Font
- Poetry integration for dependency management
- Python interpreter auto-detection

### Fun Welcome Experience

The environment includes a delightful welcome message using:
- `fortune` - Random quotes and sayings
- `cowsay` - ASCII art cow speech bubbles  
- `lolcat` - Rainbow colored output

## 🚦 Getting Started

### Prerequisites

1. **Coder Platform Access**: Ensure you have access to a Coder deployment
2. **AWS Credentials**: Your Coder admin should have configured AWS access
3. **Template Deployment**: The AWS Linux EC2 Container template should be available

### Creating Your Workspace

1. **Access Coder Dashboard**
   ```
   https://your-coder-instance.com
   ```

2. **Create New Workspace**
   - Select "AWS Linux EC2 Container" template
   - Choose your desired EC2 instance type
   - Configure workspace name and settings

3. **Wait for Provisioning**
   - AWS EC2 instance creation (~2-3 minutes)
   - Container image building and startup (~3-5 minutes)
   - Development environment initialization

4. **Access Your Environment**
   - Click "VS Code" to open the web-based editor
   - Or use SSH/terminal access for command-line work

### Running the Sample Application

Once your workspace is ready:

1. **Open Terminal** in VS Code or via Coder dashboard

2. **Install Dependencies**
   ```bash
   poetry install
   ```

3. **Run the Sample App**
   ```bash
   python main.py
   ```

   Expected output:
   ```
   <Record works='works'>
   ```

This confirms the Python application successfully connected to PostgreSQL.

## 🔧 Customization Options

### Adding Python Dependencies

Edit `pyproject.toml`:
```toml
[tool.poetry.dependencies]
python = "^3.12"
asyncpg = "^0.29.0"
# Add your dependencies here
requests = "^2.31.0"
fastapi = "^0.104.0"
```

Then run:
```bash
poetry add <package-name>
```

### VS Code Extensions

Modify `.devcontainer/devcontainer.json`:
```json
{
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-python.python",
        "ms-python.vscode-pylance",
        "ms-vscode.vscode-json"
      ]
    }
  }
}
```

### Database Configuration

Update environment variables in `docker-compose.yml`:
```yaml
environment:
  POSTGRES_DB: myapp
  POSTGRES_USER: developer
  POSTGRES_PASSWORD: secure_password
```

## 💡 Key Benefits for Development Teams

### 🌩️ **Cloud-Native Development**
- No local environment setup required
- Consistent development environments across team
- Access from any device with a web browser

### ⚡ **Instant Provisioning**
- New team members productive in minutes
- Experiment with different configurations safely
- Spin up environments for feature branches

### 🔒 **Security & Compliance**
- Code never leaves your cloud infrastructure
- Centralized access control and monitoring
- Automatic environment cleanup and resource management

### 💰 **Cost Optimization**
- Pay only for active development time
- Automatic workspace hibernation when idle
- Right-size compute resources per project needs

## 🎯 Use Cases

This template is ideal for:

- **Python Web Development** with database requirements
- **Data Science Projects** needing PostgreSQL connectivity
- **API Development** with FastAPI, Django, or Flask
- **Database-driven Applications** requiring persistent storage
- **Team Onboarding** with zero local setup requirements

## 📚 Next Steps

1. **Explore the Coder Documentation**: [docs.coder.com](https://docs.coder.com)
2. **Customize the Template**: Modify containers for your specific needs
3. **Set Up CI/CD Integration**: Connect with your deployment pipelines
4. **Configure Team Templates**: Create organization-specific environments

## 🤝 Support

For questions about this template or Coder in general:
- **Coder Documentation**: [docs.coder.com](https://docs.coder.com)
- **Community Discord**: [coder.com/chat](https://coder.com/chat)
- **GitHub Issues**: [github.com/coder/coder](https://github.com/coder/coder)

---

**Ready to revolutionize your development workflow?** This template demonstrates just the beginning of what's possible with Coder's cloud development environments.