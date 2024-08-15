# Make your own image

When you have made modifications to an image and want to create your own image, you can follow the steps below on Linux to create a minimal image.

1. Firstly, use the `gparted` software to open the SD card of the image you want to create. Use `gparted` to partition the unused space and set it as unallocated. This ensures that this portion of empty space without any valid content is not included in the image creation.
   ![Image title](assets/images/make-image/gparted.png){width="400"}

2. Next, use the `fdisk` command to view the size of the available space, as shown in the following image, which is 10151935.
   ![Image title](assets/images/make-image/fdisk.png){width="400"}

3. Then, use the `dd` command to write to an empty img file. Set the `count` value to be greater than the size of the volume end obtained from `fdisk` by at least 1.

```bash
touch blikvm-armbian-v4-20230623.img
sudo dd if=/dev/sdb of=./blikvm-armbian-v4-20230623.img bs=512 count=10151936
```

4. Wait for the `dd` command to finish executing.
