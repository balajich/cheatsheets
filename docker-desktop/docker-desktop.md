# Intro
Docker Desktop helps to run docker on windows using WSL (Windows SubSystem for Linux)
# Increase vm.max_map_count 
    open powershell
    wsl -d docker-desktop
    sysctl -w vm.max_map_count=262144