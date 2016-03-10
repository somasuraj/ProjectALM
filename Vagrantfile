Vagrant.configure(2) do |config|

  config.vm.network "public_network"
 
  config.vm.define "server" do |server|
    server.vm.box = "ubuntu/trusty64"
    server.vm.network "forwarded_port", guest: 80, host: 3333

    server.vm.provision "chef_client" do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/cybagesoftware"
      chef.validation_key_path = "cybagesoftware-validator.pem"
      chef.validation_client_name = "cybagesoftware-validator"
      chef.node_name = "server"
      chef.delete_node = true
      chef.delete_client = true
      chef.add_recipe "apache2::default"
    end

  end
  
end