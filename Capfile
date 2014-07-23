server "puppet-test.jbrunton.com", :web, user: "root"

task :puppet_install do
  run "cd /root"
  run "wget http://apt.puppetlabs.com/puppetlabs-release-precise.deb"
  run "sudo dpkg -i puppetlabs-release-precise.deb"
  run "sudo apt-get update && sudo apt-get -y install puppet-common"
  run "rm puppetlabs-release-precise.deb"
end

task :puppet_install_modules do
  run "puppet module install puppetlabs-apache"
end

task :copy_manifest do
  upload "puppet/manifests/default.pp", "/root", :via => :scp
end

task :puppet_apply do
  run "cd /root"
  run "puppet apply default.pp"
  run "rm default.pp"
end

desc "provision the server"
task :provision do
  puppet_install
  puppet_install_modules
  copy_manifest
  puppet_apply
end
