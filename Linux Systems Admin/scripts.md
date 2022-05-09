## Backup
    
    # Using this will create a backup

    # We can use gzip to compress a file and turn it in to a gzip. 
        ex: 
            gzip {filename}.tar
    
    # Creating a backup in to a location with tar. 
        ex:
            tar cvf /var/backup/{nameoffile}.tar /home

    # To see how much memory is left in your machine and save it in a location. 
        ex:
            free -h > /var/backup/desk_space.txt

## Cleanup

    # Cleaning up temporary directories 
        ex:
            apt clean -y 

## To update programs and packages

    # Checking current updates and upgrade
        apt update -y 
    # Install and uninstalling old packages
        apt full-upgrade -y
    #Removing a package
        apt autoremove --purge -y 
    


