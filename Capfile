server "puppet-test.jbrunton.com", :web, user: "root"

namespace :puppet do
  task :install do
    run "cd /root"
    run "wget http://apt.puppetlabs.com/puppetlabs-release-precise.deb"
    run "sudo dpkg -i puppetlabs-release-precise.deb"
    run "sudo apt-get update && sudo apt-get -y install puppet-common"
    run "rm puppetlabs-release-precise.deb"
  end

  task :install_modules do
    run "puppet module install puppetlabs-apache"
  end

  task :copy_manifest do
    upload "puppet/manifests/default.pp", "/root", :via => :scp
  end

  task :apply do
    run "cd /root"
    run "puppet apply default.pp"
    run "rm default.pp"
  end
  
  task :provision do
    install
    install_modules
    copy_manifest
    apply
  end
end


desc "provision the server"
task :provision do
  puppet.provision
end
