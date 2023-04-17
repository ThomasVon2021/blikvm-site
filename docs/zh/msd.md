# **U盘设备模拟**

BliKVM支持U盘设备模拟，通过此功能可以进行远程挂载镜像，进行重装系统。

## 手动 (不使用Web UI)

!!! info "1. 确认系统存在下面4个路径。如果你使用的是最新的BliKVM镜像，无需进行检查。其中/opt/bin/msd/user路径用于存放系统镜像。"
    ```
	/usr/bin/blikvm/ventoy-1.0.88
	/usr/bin/blikvm/kvmd-msd.sh
	/opt/bin/msd/user    
	/opt/bin/msd/ventoy
    ```

!!! info "2. 通过SSH登陆到BliKVM终端，用户名和密码均为blikvm，通过rw命令，使只读系统变为可写系统。"
    ```
        sudo rw
    ```

!!! info "3. 在你控制端的电脑，可以在终端使用下列命令，将iso镜像文件拷贝到BliKVM镜像的指定路径下。"
    ```
        scp ***.iso blikvm@xxx.xxx.xxx.xxx:/opt/bin/msd/user/
    ```	
!!! warning "当然，你也可以通过其他任何你熟悉的方式将iso镜像文件拷贝到指定路径下。"
	
!!! info "4. 通过使用下列两种命令中的一个，将镜像拷贝到模拟的U盘中。U盘默认大小设置的为5GB，如果你需要更大的空间，你需要修改kvmd-msd.sh脚本。"
    - 如果 /opt/bin/msd/user 路径下只有一个镜像文件, 你可以直接使用此命令. 
    ```
        sudo bash /usr/bin/blikvm/kvmd-msd.sh make
    ```
    - 如果 /opt/bin/msd/user 路径下有不止一个镜像文件, 你可以使用下列文件指定. **xxx.iso** 表示镜像的名称.
    ```
       	sudo bash /usr/bin/blikvm/kvmd-msd.sh make xxx.iso
    ```

!!! warning "cp过程非常慢，请耐心等待执行完成。"

!!! info "5. 如果你需要扩大模拟的U盘大小，在kvmd-msd.sh文件里找到"sudo dd if=/dev/zero of=ventoy.img bs=1M count=5120 status=progress;" 这一行, 修改"count=5120"为你想要的值，注意SD卡的大小 "

!!! info "6. 运行下列命令，将模拟的U盘连接到到你的被控设备上"
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh conn
    ```

!!! info "7. 运行下列命令，将模拟的U盘从你的被控设备上弹出"		
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh disconn
    ```

!!! info "8. 运行下列命令，清除掉模拟的U盘，将会释放掉对应的空间"		
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh clean
    ```


!!! info "9. 一切正确的话，此时你可以在一个PC系统里看到你模拟出的U盘。通过WEB重启的你的PC，然后使用快捷键（很多电脑是按F2）进入BIOS，修改boot启动优先级，将模拟出的U盘设备优先级设置在最前面。"		


!!! info "10. 根据bios系统提示，保存重启，即可进行ventoy的引导界面进行重装系统。"		

## 使用Web UI
developing.