
# Vagrant.configure("2") do |config|

#   config.vm.box = "centos/7"
  
# end

# Couldn't install the ansible package on the centos/7 box. So, I had to install the epel-release package first and then install the ansible package.
# Vagrant.configure("2") do |config|

#   config.vm.define "ansible-controller" do |controller|
#     controller.vm.hostname = "controller"
#     controller.vm.box = "centos/7"
#     controller.vm.provision "shell", inline: <<-SHELL
#       sudo yum install epel-release -y
#       sudo yum install ansible -y
#     SHELL
#   end
# end

# SECOND WAY TO INSTALL ANSIBLE PACKAGE
Vagrant.configure("2") do |config|
  config.vm.define "ansible-controller" do |controller|
    controller.vm.hostname = "controller"
    controller.vm.box = "centos/7"
    
    # Ensure network connectivity
    #controller.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)" # Adjust for your network interface
    
    # Provisioning steps
    controller.vm.provision "shell", inline: <<-SHELL
      # Fix DNS issues for CentOS in WSL
      echo 'nameserver 8.8.8.8' | sudo tee /etc/resolv.conf > /dev/null
      
      # Ensure the system is updated
      sudo yum clean all
      sudo yum makecache fast
      sudo yum update -y

      # Install EPEL repository and Ansible
      sudo yum install -y epel-release
      sudo yum install -y ansible python3
    SHELL
  end
end

