# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "centos64"
  config.vm.forward_port 88, 8080

  config.vm.provision :chef_solo do |chef|
    # This path will be expanded relative to the project directory
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe("main")
    chef.json.merge!({
      :rvm => {
        :rvmrc => {
          :rvm_gemset_create_on_use_flag => 1,
          :rvm_trust_rvmrcs_flag => 1
        }
      },
      :mysql => {
        :server_root_password => "alfresco",
        :server_repl_password => "alfresco",
        :server_debian_password => "alfresco"
      }
    })

  end

end
