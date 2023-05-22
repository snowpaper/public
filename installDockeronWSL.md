# How to install WSL, Docker

## Step 1: Install WSL 2

1. Open PowerShell as an administrator.
-> Press the Windows key, type "PowerShell," right-click on "Windows PowerShell," and select "Run as administrator."
2. Enable the Windows Subsystem for Linux (WSL) feature by running the following command in the PowerShell window:

```
wsl --install
```
3. Wait for the installation process to complete. It may take a few minutes.
4. Once the installation is finished, you'll be prompted to restart your computer. Type "y" and press Enter to proceed with the restart.
5. After the restart, open the Microsoft Store.
6. Search for a Linux distribution of your choice, such as "Ubuntu" or "Debian," and select the one you prefer.
7. Click the "Install" button to download and install the Linux distribution.
8. Wait for the installation to complete. This process may take a few minutes.
9. Launch the Linux distribution from the Start menu or by searching for its name.
10. Wait for the Linux distribution to initialize and set up a new user account. Provide a username and password when prompted.

With WSL 2 installed and a Linux distribution set up, you can proceed with Step 2 from my previous response to install Docker on WSL 2.

## Step 2: Install Docker on WSL 2

1. Open a terminal within your WSL 2 Linux distribution (e.g., Ubuntu or Debian).
2. Update the package lists and install the necessary dependencies by running the following commands:
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
3. Add Docker's official GPG key by executing the following command:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
Note: If you're using a different Linux distribution, replace ubuntu in the URL with the appropriate distribution name. For example, debian for Debian.

4. Add the Docker repository by running the following command:
```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
Note: If you're using a different Linux distribution, replace ubuntu in the URL with the appropriate distribution name.

5. Update the package lists again:
```
sudo apt update
```
6. Install Docker by running the following command:
```
sudo apt install docker-ce docker-ce-cli containerd.io
```
7. Start the Docker service:
```
sudo service docker start
```

## Step 3: Configure Docker CLI to use Docker on WSL 2

1. Open a terminal within your WSL 2 Linux distribution.
2. Add your Linux user to the docker group, which allows you to run Docker commands without using sudo. Execute the following command:
```
sudo usermod -aG docker $USER
```
Note: Replace `$USER` with your Linux username.

3. Log out of your WSL 2 session and log back in to apply the group changes.
4. Verify that Docker is working correctly by running the following command:
```
docker run hello-world
```
This command should download and run a small test container, displaying a "Hello from Docker!" message if everything is set up properly.

After completing these steps, you should have Docker installed and configured on WSL 2, allowing you to use Docker commands from within the Linux environment.
