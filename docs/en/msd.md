# **Mass Storage Drive**

BliKVM supports USB device simulation, which allows for remote mounting of images and system reinstallation.

## Manually (without Web UI)

!!! info "1. Confirm that the following four paths exist. If you are using the official latest image of blikvm, and it is fully configured, there is no need to check. The/opt/bin/msd/user path is used to store images."
    ```
	/usr/bin/blikvm/ventoy-1.0.88
	/usr/bin/blikvm/kvmd-msd.sh
	/opt/bin/msd/user    
	/opt/bin/msd/ventoy
    ```

!!! info "2. SSH logs in to blikvm, executes the rw command, and changes the system permission to writable."
    ```
        sudo rw
    ```

!!! info "3. In your PC ,use scp cmd send iso file to kvm board."
    ```
        scp ***.iso blikvm@xxx.xxx.xxx.xxx:/opt/bin/msd/user/
    ```	
!!! warning "Of course, you can also use any other familiar method to upload the image to the specified path."
	
!!! info "4. excute msd cmd.wait until excute end. The default size of the USB flash disk is 5GB, if your iso is large than 5GB, you should modify kvmd-msd.sh."
    - If /opt/bin/msd/user this path only have one iso, you can use the follow command. 
    ```
        sudo bash /usr/bin/blikvm/kvmd-msd.sh make
    ```
    - If /opt/bin/msd/user this path have more than one iso, you can use the follow command. **xxx.iso** means the iso name.
    ```
        sudo bash /usr/bin/blikvm/kvmd-msd.sh make xxx.iso
    ```

!!! warning "cp progress slowly, Please be patient."

!!! info "5. If you want to expand the USB flash size, find "sudo dd if=/dev/zero of=ventoy.img bs=1M count=5120 status=progress;" this line in kvmd-msd.sh, change the "count=5120". "

!!! info "6. connect msd"
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh conn
    ```

!!! info "7. disconnect msd"		
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh disconn
    ```

!!! info "8. clean msd"		
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh clean
    ```

!!! info "9. throuht web restart PC, enter BIOS, modify boot priority,set blikvm USB first."		


!!! info "10. according to step, select operate system , format partition and install system."		

## With Web UI
developing.