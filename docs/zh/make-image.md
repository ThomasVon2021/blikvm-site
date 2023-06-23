# Make your owner image

当你对镜像进行了修改，想制作自己的镜像时，可以参考下面在linux下的方法，制作一个最小镜像。  

1. 首先使用gparted软件，打开所要制作的镜像的sd卡。将未使用的空间通过gparted软件将其分割出来，并将其设置为未分配。这样制作镜像时，这部分无任何有效内容的空间就不会被制作了。  
![Image title](assets/images/make-image/gparted.png){width="400"}

2. 然后使用首先使用fdisk命令查看有效空间的大小，如下图,即10151935。    
![Image title](assets/images/make-image/fdisk.png){width="400"}

3. 然后使用dd命令往一个空的img文件里写入即可,其中count的大小比fdisk看到的卷尾大小大于1即可。
```
touch blikvm-armbian-v4-20230623.img
sudo dd if=/dev/sdb of=./blikvm-armbian-v4-20230623.img bs=512 count=10151936
```

4. 等待dd命令执行完成即可。
