# devcontainer

### Introduction
This repository provides a boilerplate for setting up a development container (devcontainer) for Ruby projects. Devcontainers offer a fully configured development environment with consistent tooling and dependencies, making it easier to onboard new developers and work across different machines.

### Prerequisites
- Docker
- Visual Studio Code with the Remote - Containers extension

### Repository Structure
- ``.devcontainer/devcontainer.env``: Environment variables for the devcontainer.
- ``.devcontainer/devcontainer.json``: Configuration file for VS Code to set up the development container.
- ``.devcontainer/docker-compose.yml``: Docker Compose file to define and run multi-container Docker applications.
- ``.devcontainer/Dockerfile``: Instructions for building the Docker image for the development environment.
- ``.devcontainer/post-create.sh``: A script that runs after creating the container to set up or configure additional components.

### Setup Instructions
1. Clone this repository or copy the files into your Ruby project.
2. Open your project with Visual Studio Code.
3. Use the Remote - Containers extension to open your project in a container.
4. Modify the files in the .devcontainer directory as necessary to suit your project's needs.

### Configuration Details
- ``devcontainer.json``: Customize settings such as the name of your project, ports to forward, and post-create commands.
- ``Dockerfile``: Update this file to add additional dependencies or alter the development environment.
- ``docker-compose.yml``: Modify this file if you need to add more services like databases or caching systems.

### Common Use Cases
This boilerplate is useful for:

- Standardizing development environments across different machines.
- Quickly setting up new developers with all the necessary dependencies and tooling.
- Isolating development dependencies from your local environment.

### Contributing
Contributions are welcome! If you have suggestions or improvements, please open an issue or submit a pull request.
