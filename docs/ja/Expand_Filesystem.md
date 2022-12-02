# ファイルシステムの拡張
Raspberry Piで使用中のSDカードやeMMCの容量が実際のSDカードやeMMCの最大容量よりも少ない場合には、下記の操作を行うことにより最大容量まで使用できます。

**1.** raspi-configを実行
```
sudo raspi-config
```
**2.** Advancd Options を選択：  
![IMG_8366](assets/images/expand_filesystem/advance_option.png){width="300"}

**3.** Expand Filesystem を選択：  
![IMG_8366](assets/images/expand_filesystem/expand.png){width="300"}

**4.** Ok:  
![IMG_8366](assets/images/expand_filesystem/expand_ok.png){width="300"}

**5.** Raspberry Piを再起動
