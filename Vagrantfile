
# # Vagrant.configure("2") do |config|

# #   config.vm.box = "centos/7"
  
# # end

# # Couldn't install the ansible package on the centos/7 box. So, I had to install the epel-release package first and then install the ansible package.
# # Vagrant.configure("2") do |config|

# #   config.vm.define "ansible-controller" do |controller|
# #     controller.vm.hostname = "controller"
# #     controller.vm.box = "centos/7"
# #     controller.vm.provision "shell", inline: <<-SHELL
# #       sudo yum install epel-release -y
# #       sudo yum install ansible -y
# #     SHELL
# #   end
# # end

# # Grab the name of the default interface
# $default_network_interface = `ip route | awk '/^default/ {printf "%s", $5; exit 0}'`

# # SECOND WAY TO INSTALL ANSIBLE PACKAGE
# Vagrant.configure("2") do |config|
#   config.vm.define "ansible-controller" do |controller|
#     controller.vm.hostname = "controller"
#     controller.vm.box = "centos/7"
#     # Specify the interface when creating the public network
#     config.vm.network "public_network", bridge: "#$default_network_interface"
    
#     # Ensure network connectivity
#     #controller.vm.network "public_network", bridge: "en0: Wi-Fi (AirPort)" # Adjust for your network interface
    
#     # Provisioning steps
#     controller.vm.provision "shell", inline: <<-SHELL
#       # Fix DNS issues for CentOS in WSL
#       # echo 'nameserver 8.8.8.8' | sudo tee /etc/resolv.conf > /dev/null
      
#       # Ensure the system is updated
#       sudo yum clean all
#       sudo yum makecache fast
#       sudo yum update -y

#       # Install EPEL repository and Ansible
#       sudo yum install -y epel-release
#       sudo yum install -y ansible python3
#     SHELL
#   end
# end

# SWITCHING TO UBUNTU OS

Vagrant.configure("2") do |config|
  
  # VirtualBox provider configurations
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true # Display the VirtualBox GUI when booting the machine
    vb.memory = "2048" # Set memory for the VM
    vb.cpus = "2" # Set the number of CPUs
  end

  # Define the VM
  config.vm.define "UbuntuVM" do |subconfig|
    subconfig.vm.box = "ubuntu/focal64" # Use Ubuntu 20.04 (Focal Fossa) box
    subconfig.vm.hostname = "UbuntuVM" # Set hostname

    # Configure a public network
    subconfig.vm.network "public_network"

    # Provision the VM with required packages
    subconfig.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y ansible python3
    SHELL
  end
end
