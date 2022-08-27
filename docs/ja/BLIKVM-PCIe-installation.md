# BLIKVM PCIe CM4 組み立てガイド

![PCIe_main](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/PCIe_main.jpg){width="500"}
## **1.開封してデバイスを取り出してください**
!!! note "製品一覧"
    ![PCIe_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/PCIe_all.jpg){width="400"}

## **2.主要デバイスの組み立て**
!!! note "Raspberry Pi CM4と4つの六角スペーサを設置してください。(ここではCM4 Liteを例として使用しています。そして、microSDカードを使用します。eMMCを利用する場合は別途イメージの書き込みを行なってください)熱伝導シートをCM4に貼り付けて、保護フィルムをシートから剥がしてください。"
    ![Preparing_to_install_CM4](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Preparing_to_install_CM4.jpg){width="300"}
    ![install_cm4_and_4_spacers](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_cm4_and_4_spacers.jpg){width="300"}
    ![install_cm4_and_4_spacers_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_cm4_and_4_spacers_2.jpg){width="300"}
    ![Stick_a_heat_conductive_sheet](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Stick_a_heat_conductive_sheet.jpg){width="300"}   

    ヒートシンクの設置。4本のネジで先に設置した六角スペーサに固定してください。

    ![Install_metal_heatsink](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_metal_heatsink.jpg){width="300"}

**主要デバイスの組み立ては完了です**

## **3.USBとATXの接続**
!!! note "ここではAsus H520-Eを使って説明しています。インターフェイスの位置や配列はマザーボードごとに異なります。実際に使用するマザーボードのマニュアルを参照して接続してください。"
    ![connection_preparation](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connection_preparation.jpg){width="300"}
    ![connect_USB_and_ATX](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX.jpg){width="300"}
    ![connect_USB_and_ATX_motherborad](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX_motherborad-165941489982915.jpg){width="300"}
    ![pin_definition_atx](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/pin_definition_atx.jpg){width="300"}
    ![connect_USB_and_ATX_OK](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX_OK.jpg){width="300"}

## **4.OLEDディスプレイの接続**
!!! note ""
    ![connect_OLED](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_OLED.jpg){width="400"}

## **5.HDMIケーブルの接続**
!!! note "コンピュータのHDMIポートと製品のHDMI INポートをHDMIケーブルで直に接続してください。HDMIパススルーEDIDエミュレータは必要ありません。もし、コンピュータが正しいHDMI出力を行わない場合は、HDMIパススルーEDIDエミュレータをコンピュータのHDMI出力ポートに挿してください。これはコンピュータのHDMI出力フォーマットを修正します。"
    ![Connect_HDMI_cable_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_1.jpg){width="300"}
    ![Connect_HDMI_cable_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_2.jpg){width="300"}
    ![Connect_HDMI_cable_3](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_3.jpg){width="300"}

## **6.ネットワークケーブルの接続**
!!! note "ギガビットイーサネットポートは、IEEE 802.3af規格、電圧37-57VのPoE給電に対応しています"
    ![Connect_the_network_cable](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_the_network_cable.jpg){width="400"}

!!! warning "PoEでの給電を行う場合は、PWR-INポートは使用しません"

## **7.PWR-INの接続**

![Connect_PWR-IN](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_PWR-IN.jpg){width="400"}

!!! warning "PoEでの給電を使わない場合に5V/3AのUSB電源アダプタをPWR-INに接続してください"

## **8.テスト**

!!! note "OLEDディスプレイにデバイスのIPアドレスなどの情報が表示されます"
    ![find_IP](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/find_IP.jpg){width="300"}
    ![test_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/test_all.jpg){width="300"}  
    IPアドレスへWebブラウザからアクセスしてください。テストが完了してからボードをコンピュータへ設置してください。

## **9.製品をコンピュータのケースへ設置**

!!! note "電源を抜いてから、マザーボードへ製品を設置してください。その後にケーブルを差し直してください。"
    ![blikvm_in_case](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/blikvm_in_case.jpg){width="300"}
    ![OLED_display_out](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/OLED_display_out.jpg){width="300"}
    ![finish_installation_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/finish_installation_1.jpg){width="300"}
    ![finish_installation_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/finish_installation_2.jpg){width="300"}

楽しんでくだい！

## **補足 1.ロープロファイル PCIe I/O ブラケットの取り付け方**
!!! note
    ![remove_standard_bracket](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/remove_standard_bracket.jpg){width="300"}
    ![replace_low_bracket_1_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_1_1.jpg){width="300"}
    ![replace_low_bracket_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_2.jpg){width="300"}
    ![replace_low_bracket_3](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_3.jpg){width="300"}
    ![replace_low_bracket_4](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_4.jpg){width="300"}

## **補足 2.冷却ファンの取り付け方**

!!! note "通常であればヒートシンクだけで十分で、冷却ファンは必要ありません"
    ![install_fan_prepare](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_prepare.jpg){width="300"}
    ![install_fan_unscrew](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_unscrew.jpg){width="300"}
    ![place_4_nylon_spacers](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/place_4_nylon_spacers.jpg){width="300"}
    ![install_fan_ok](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_ok.jpg){width="300"}
    ![fan_power_polarity](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/fan_power_polarity.jpg){width="300"}
    ![install_fan_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_all.jpg){width="300"}  

!!! info "冷却ファンはCM4のGPIO12に接続されコントロールされます"

## **補足 3.Wi-Fiアンテナの取り付け方**
!!! note
    ![Install_wifi_antenna_prepare](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_wifi_antenna_prepare.jpg){width="300"}
    ![Install_wifi_antenna](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_wifi_antenna.jpg){width="300"}
