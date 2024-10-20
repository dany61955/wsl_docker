Install Docker in WSL Ubuntu
Update and Install Dependencies: Open your WSL Ubuntu terminal and run:

bash
Copy code
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
Add Docker’s Official GPG Key:

bash
Copy code
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
Set up the Docker Repository:

bash
Copy code
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
Install Docker Engine:

bash
Copy code
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Start Docker: To start Docker automatically each time, you can add the following configuration. In WSL 2, Docker requires manual configuration:

bash
Copy code
sudo service docker start
Test the Docker Installation:

bash
Copy code
sudo docker run hello-world
Optional: Run Docker without sudo
If you want to run Docker as a non-root user (without sudo):

bash
Copy code
sudo groupadd docker
sudo usermod -aG docker $USER
After this, log out and back in or restart WSL for the group changes to take effect:

bash
Copy code
newgrp docker
