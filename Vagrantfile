Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end

  config.vm.define :pgclient do |pgclient|
#   pgclient.vm.box = "bento/centos-6.10"
#   pgclient.vm.box = "clouddood/RH7.5_baserepo"
    pgclient.vm.box = "clouddood/RH7.5_baserepo"
    pgclient.vm.host_name = "pgclient.test.dev"

    pgclient.ssh.forward_agent = true

    pgclient.vm.provision "ansible" do |ansible|
#     ansible.playbook = "deploy_Postgresql_client.yml"
#     ansible.playbook = "deploy_Postgresql_client_DEV.local.yml"
      ansible.playbook = "deploy_BaseSystem.yml"
      ansible.inventory_path = "vagrant_hosts"
#     ansible.tags = ansible_tags
#     ansible.verbose = ansible_verbosity
#     ansible.extra_vars = ansible_extra_vars
#     ansible.limit = ansible_limit
    end

#   pgclient.vm.network :private_network, ip: "10.0.1.26"
    pgclient.vm.network :private_network, ip: "192.168.56.128"
  end

#######################################################################################################################################

# config.trigger.before :destroy do |trigger|
#   run "rm -Rf /tmp/abc/*"
    # subscription-manager remove --all
    # subscription-manager unregister
    # subscription-manager clean
#   trigger.name = "Destroy Trigger ..."
#   trigger.info = "Destroy Trigger Execution ..."
#   trigger.run = { path: "subscription-manager remove --all"}
#   trigger.run = { path: "subscription-manager unregister"}
#   trigger.run = { path: "subscription-manager clean"}
# end
end
