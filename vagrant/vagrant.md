# Vagrant commands
    vagrant up
    vagrant ssh
    # To halt the machine – that is, attempt a graceful shut down
    vagrant halt
    # A suspended machine is a machine that is turned off but not shut down; essentially, it is saved in the exact state that it was in when the suspend was run
    vagrant suspend
    # To start a previously-halted or suspended machine, run:
    vagrant resume
    # Restart
    vagrant restart
    # Want to fully remove it from your system
    vagrant destroy
    #outputs status of all vagrant machines
    vagrant global­-status
    # but prunes invalid entries
    vagrant global­-status --prune
# Vagrant Boxes
    vagrant box list
# References
    https://linuxacademy.com/blog/linux/vagrant-cheat-sheet-get-started-with-vagrant/
    https://cheatography.com/davbfr/cheat-sheets/vagrant-cheat-sheet/