# PiVirt Cloud Agent

A cloud agent for the PiVirt virtualization platform.

Supported Operating Systems:
- Linux (Specific distributions listed below)

See [https://pilab.hu/products/pivirt](https://pilab.hu/products/pivirt) for more information about the PiVirt platform.

## Installation

### Debian (Bullseye)

```bash
sudo apt-get update
sudo apt-get install pivirt-agent=<specific_package_version> # Example: pivirt-agent=1.2.3-1
```

### Fedora/RHEL/CentOS/Red Hat/Oracle/AlmaLinux

Create a file `/etc/yum.repos.d/pivirt-agent.repo` with the following content:

```ini
[pilab]
name=PiLab RPM Repository
baseurl=[https://dl.pilab.hu/rpm/](https://dl.pilab.hu/rpm/)
enabled=1
gpgcheck=1
```

Then, install the agent using the appropriate package manager:

```bash
# Fedora/CentOS 8+ / RHEL 8+ / AlmaLinux 8+
sudo dnf install pivirt-agent

# CentOS 7 / RHEL 7 / Oracle Linux 7
sudo yum install pivirt-agent
```

## Configuration

The configuration file is located at `/etc/pivirt/agent.conf`.

**Authentication:**

The agent uses certificate-based authentication. You can generate certificates using the `pivirt-certgen` tool.

```bash
pivirt-certgen --agent=$(hostname) --output-dir /etc/pivirt # Example usage, add other options if needed
```

This will generate `cert.pem` (certificate) and `key.pem` (private key) in `/etc/pivirt/`.

**Example `agent.conf`:**

```ini
[agent]
api_address = 127.0.0.1:8080 # The address and port the agent listens on
cert_path = /etc/pivirt/cert.pem
key_path = /etc/pivirt/key.pem
# Add other configuration options with explanations
log_level = INFO #DEBUG, WARNING, ERROR, CRITICAL
```

**Configuration Options:**

*   `api_address`: The RPC server address and port.
*   `cert_path`: The path to the certificate files.
*   `log_level`: The logging level. Default is `INFO`.

## Usage

The agent runs as a headless daemon in the background and provides an RPC API for controlling the PiVirt platform.

**RPC Interface Functionality:**

*   List key functionalities of the API (e.g., "Start/Stop VMs," "Get VM status," "Manage network interfaces").

## Troubleshooting

*   **Problem:** (Description of the problem)
    *   **Solution:** (How to fix it)
*   *(Add more troubleshooting entries)*

## Logging

The agent logs to `/var/log/pivirt-agent.log`. You can adjust the logging level in the `agent.conf` file.

## License

All Rights Reserved to the PiVirt creators.

<p align="center">
Sponsored with ❤️ by
</p>
<p align="center">
    <a href="https://newpush.com" target="_blank">
    <img src="https://www.newpush.com/images/np_logo_blue_SVG.svg" width="128"/>
    </a><br>
    We focus on reliability, quality, and value.
</p>
