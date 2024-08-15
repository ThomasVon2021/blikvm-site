# **U盘设备模拟**
!!! info "重装系统视频"
    <iframe src="//player.bilibili.com/player.html?aid=227573682&bvid=BV1yh41177A6&cid=1099326734&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

BliKVM支持U盘设备模拟，通过此功能可以进行远程挂载镜像，进行重装系统。

## Web UI
msd虚拟U盘入口为:
![](assets/images/msd/web-ui.png)

!!! warning "使用web上传镜像和制作启动盘，均是同步线程，上传镜像退出MSD的UI界面后，下次再选择相同镜像可断点续传。制作启动盘推出后不可断点重做，需重新开始。"
    - 上传镜像默认路径为/mnt/upload,若出现上传失败，删除为成功的缓存文件，可手动删除此文件夹；
    - 因部分镜像文件大小较大，采取上传镜像方案为切片上传和合并，合并过程不能断点重来，切记等待合并完成后(时间较长)，再进入下一步；  
    - 制作启动盘也很为两个步骤，制作虚拟U盘，将选择的iso镜像拷贝到制作好的虚拟U盘里，两个步骤均有进度，请等两者进度均100%后再点击下一步按钮。  
    ![](assets/images/msd/progress.png){width="300"}
    ![](assets/images/msd/merger.png){width="300"}
    
## 手动 (不使用Web UI)

!!! info "1. 确认系统存在下面4个路径。如果你使用的是最新的BliKVM镜像，无需进行检查。其中/opt/bin/msd/user路径用于存放系统镜像。"
    ```
	/usr/bin/blikvm/ventoy-1.0.88
	/usr/bin/blikvm/kvmd-msd.sh
	/mnt/msd/user    
	/mnt/msd/ventoy
    ```

!!! info "2. 通过SSH登陆到BliKVM终端，用户名和密码均为blikvm，通过rw命令，使只读系统变为可写系统。"
    ```
        sudo rw
    ```

!!! info "3. 在你控制端的电脑，可以在终端使用下列命令，将iso镜像文件拷贝到BliKVM镜像的指定路径下。"
    ```
        scp ***.iso blikvm@xxx.xxx.xxx.xxx:/mnt/msd/user/
    ```	
!!! warning "当然，你也可以通过其他任何你熟悉的方式将iso镜像文件拷贝到指定路径下。"
	
!!! info "4. 通过使用下列两种命令中的一个，将镜像拷贝到模拟的U盘中。U盘默认大小设置的为5GB，如果你需要更大的空间，你需要修改kvmd-msd.sh脚本。"
    - 如果 /mnt/msd/user 路径下只有一个镜像文件, 你可以直接使用此命令. 
    ```
       sudo bash /usr/bin/blikvm/kvmd-msd.sh -c make
    ```
    - 如果 /mnt/msd/user 路径下有不止一个镜像文件, 你可以使用下列文件指定. **xxx.iso** 表示镜像的名称.其中-s后跟的数字即是制作的U盘的大小，单位是G，用户可以根据自己需求修改。-n后跟的字符串是u盘名称。
    ```
       	sudo bash /usr/bin/blikvm/kvmd-msd.sh -c make -s 5 -n ventoy -f xxx.iso
    ```

!!! warning "cp过程非常慢，请耐心等待执行完成。"

!!! info "5. 运行下列命令，将模拟的U盘连接到到你的被控设备上"
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh -c conn
    ```

!!! info "6. 运行下列命令，将模拟的U盘从你的被控设备上弹出"		
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh -c disconn
    ```

!!! info "7. 运行下列命令，清除掉模拟的U盘，将会释放掉对应的空间"		
    ```
        sudo bash  /usr/bin/blikvm/kvmd-msd.sh -c clean
    ```


!!! info "8. 一切正确的话，此时你可以在一个PC系统里看到你模拟出的U盘。通过WEB重启的你的PC，然后使用快捷键（很多电脑是按F2）进入BIOS，修改boot启动优先级，将模拟出的U盘设备优先级设置在最前面。"		


!!! info "9. 根据bios系统提示，保存重启，即可进行ventoy的引导界面进行重装系统。"	

## 通用U盘
传递通用文件，注意文件名需命名为英文，中文会乱码。  conn， disconn, clean命令针对通用U盘依旧有效。
### 制作通用U盘
-s后跟的是制作通用U盘的大小，单位为Gb，容量越大，制作时间越长，请结合实际情况设置。 -t 必须为other
```
sudo bash /usr/bin/blikvm/kvmd-msd.sh -c make -s 4 -t other
```
### 文件从用户电脑==》KVM==》被控电脑

1. 首先你需要将文件从用户控制电脑发送到kvm
```
scp xxx blikvm@xxxx:/mnt/msd/user/
```
2. 将文件同步到被控电脑，并连接上电脑
```
sudo bash /usr/bin/blikvm/kvmd-msd.sh -c forward
```
后面有需要新的内容从用户电脑，传递到被控电脑，重复第1和第2步即可

### 文件从被控电脑==》KVM==用户电脑
1. 首先在被控电脑上将文件拷贝到模拟的虚拟U盘里，然后执行下面的指令，将文件拷贝到kvm的/mnt/msd/user/目录下
```
sudo bash /usr/bin/blikvm/kvmd-msd.sh -c rever
```
2. 将文件从kvm拷贝到用户电脑
```
scp blikvm@xxxx:/mnt/msd/user/*  .
```
   
