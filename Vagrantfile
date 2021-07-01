# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
    # Web Machine
    config.vm.define "web" do |web|
        web.vm.box = "bento/ubuntu-18.04"
        web.vm.network "private_network", ip: "192.168.33.11"
        web.vm.hostname = "web"
        web.vm.provider "virtualbox" do |vb|
			vb.customize ["modifyvm", :id, "--name", "web"]
			vb.memory = "1024"
        end
        web.vm.provision "shell", run: "always", inline: <<-SHELL
            echo "Installing Docker"
			sudo su
			apt-get update
			apt-get install \
    		apt-transport-https \
    		ca-certificates \
    		curl \
    		gnupg \
    		lsb-release
			curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
			echo \
  			"deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  			$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
			apt-get update
			apt-get install docker-ce docker-ce-cli containerd.io -y
			apt-cache madison docker-ce
			docker ps
			echo "docker installed"
		SHELL
	end
# Setup Machine
    config.vm.define "setup" do |setup|
        setup.vm.box = "bento/ubuntu-18.04"
        setup.vm.network "private_network", ip: "192.168.33.10"
        setup.vm.hostname = "setup"
        setup.vm.provider "virtualbox" do |vb|
            vb.customize ["modifyvm", :id, "--name", "setup"]
            vb.memory = "1024"
        end
        setup.vm.provision "shell", run: "always", inline: <<-SHELL
            echo "Installing Ansible"
            sudo su
            apt install sshpass -y
            apt-get install software-properties-common -y
            apt-add-repository ppa:ansible/ansible -y
            apt-get update -y
            apt-get install ansible -y
            apt update

            echo "Ansible Galaxy"
            ansible-galaxy collection install community.docker
            
            echo "Run Playbook"
        SHELL
    end
end