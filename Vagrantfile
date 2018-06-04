Vagrant.configure(2) do |config|
    machines = %w(
                    bento/ubuntu-18.04
                    bento/ubuntu-16.04
                    bento/ubuntu-14.04
                    bento/centos-6.9
                    bento/centos-7.3
                    bento/fedora-26
                    bento/debian-9.1
                 )
    machine_names = machines.map do |box|
        box.gsub(/(\/|\.)/, '-')
    end
    role_name = File.basename(File.expand_path(File.dirname(__FILE__)))
    machines.each_with_index do |box, index|
        config.vm.define machine_names[index] do |machine|
            machine.vm.box = box
            if index == machines.length - 1 then
                machine.vm.provision :ansible,
                    raw_arguments: %w(-vv --diff),
                    playbook: 'playbook.yml',
                    groups: { role_name => machine_names },
                    host_vars: { "bento-fedora-26" => {"ansible_python_interpreter" => "/usr/bin/python3"}},
                    limit: :all
            end
        end
    end
end
