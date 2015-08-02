# 
# Install, provision, configure Ubuntu precise 64 with nginx
#

Vagrant.configure("2") do | config |
  
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  
  config.vm.hostname = "nginx.demo.box"

  config.vm.network "private_network", ip: "10.2.2.15"
  config.vm.network "forwarded_port", guest: 8000, host: 8000

  config.vm.provision :chef_solo do | chef |
   chef.json = {
     :nginx => {
       :port => '8000'
     }
   }
   chef.run_list = [
     "recipe[nginx::default]",
     "recipe[newcontext-demo-site::default]"
   ]
 end


end
