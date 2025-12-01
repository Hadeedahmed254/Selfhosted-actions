# Advantages of GitHub Actions over Self-Hosted Runners

Hosting: GitHub Actions uses GitHub-managed cloud runners with no setup or maintenance required. Self-hosted runners require you to configure and maintain your own machines.

User interface: GitHub Actions works fully inside GitHub with an easy setup. Self-hosted runners need installation, machine configuration, and ongoing updates.

Cost: GitHub Actions offers free minutes for public repos and predictable pricing for private ones. Self-hosted runners require you to pay for hardware and maintenance.

# Advantages of Self-Hosted Runners over GitHub Actions

Customization: Self-hosted runners provide full control over the environment, letting you install custom tools and dependencies not available in GitHub-hosted runners.

Performance: You can use more powerful or specialized hardware to speed up builds and tests.

Environment access: Self-hosted runners can securely access internal networks, private systems, and on-prem resources that GitHub-hosted runners cannot reach.

### In conclusion, GitHub Actions is ideal for easy use and zero maintenance, while self-hosted runners offer customization, control, and access to private infrastructure.

# Create an EC2 Instance:
Allow HTTP and HTTPS on EC2:
In the EC2 Security Group, add inbound rules and outbound both:

SSH (port 22) → Source: Your IP (for secure SSH access)

HTTP (port 80) → Source: Anywhere (0.0.0.0/0)

HTTPS (port 443) → Source: Anywhere (0.0.0.0/0)
<img width="1493" height="360" alt="image" src="https://github.com/user-attachments/assets/4bb5fca1-19c9-4ae8-90f5-1c7f7ab8d852" />

### To make sure your workflows in .github/workflows run on your self-hosted runner, you need to configure both the self-hosted runner and the workflow YAML properly.

<img width="260" height="87" alt="image" src="https://github.com/user-attachments/assets/644f030b-861d-407e-8cad-a5aeeccea610" />


# Add a Self-Hosted Runner to Your Repository
Go to your repository on GitHub → Settings → Actions → Runners → Add runner.

Choose Linux (for Ubuntu EC2).

Follow the steps to download, configure, and start the runner:

#### Example commands from GitHub
mkdir actions-runner && cd actions-runner
curl -o actions-runner-linux-x64-*.tar.gz -L <download-link>
tar xzf ./actions-runner-linux-x64-*.tar.gz
./config.sh --url https://github.com/username/repo --token <TOKEN>
./run.sh

The runner will now register itself with GitHub as self-hosted.
Keep this terminal running or set it up as a service to run automatically.

<img width="1163" height="328" alt="image" src="https://github.com/user-attachments/assets/21cf9b2d-b6ba-4031-ab2c-aea932fc0354" />






