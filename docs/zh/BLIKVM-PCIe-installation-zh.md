# BLIKVM PCIe 安装说明

![PCIe_main](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/PCIe_main.jpg){width="500"}
## **1.拆开包装，拿出设备**
!!! note "产品清单"
    ![PCIe_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/PCIe_all.jpg){width="400"}

## **2.安装主体设备**
!!! note "安装CM4和4个六角螺柱(此文章使用的是CM4 lite作为列子，镜像在出厂的SD卡里已经被预装载，用户可以直接使用。若你的CM4是EMMc版本，则你需要自己烧录镜像 ，无法直接使用SD卡启动)。然后将导热片撕下保护膜，粘贴在CM4顶部。"
    ![Preparing_to_install_CM4](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Preparing_to_install_CM4.jpg){width="300"}
    ![install_cm4_and_4_spacers](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_cm4_and_4_spacers.jpg){width="300"}
    ![install_cm4_and_4_spacers_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_cm4_and_4_spacers_2.jpg){width="300"}
    ![Stick_a_heat_conductive_sheet](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Stick_a_heat_conductive_sheet.jpg){width="300"}   
    安装金属散热片。  
    ![Install_metal_heatsink](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_metal_heatsink.jpg){width="300"}

**主体设备已安装完成**

## **3.连接USB接口和ATX接口**
!!! note "此文中的主板使用的是Asus H520M-E，不同的主板接口定义不一定相同，请参考您的主板相关手册。"
    ![connection_preparation](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connection_preparation.jpg){width="300"}
    ![connect_USB_and_ATX](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX.jpg){width="300"}
    ![connect_USB_and_ATX_motherborad](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX_motherborad-165941489982915.jpg){width="300"}
    ![pin_definition_atx](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/pin_definition_atx.jpg){width="300"}
    ![connect_USB_and_ATX_OK](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_USB_and_ATX_OK.jpg){width="300"}

## **4.链接OLED显示屏**
!!! note "您收到的OLED是未安装支架的，请参考图片进行安装。另外OLED支架为亚克力材料，需要撕去表面的保护膜后使用。"
    ![connect_OLED](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/connect_OLED.jpg){width="400"}

## **5.连接HDMI线**
!!! note "将您电脑的HDMI输出口通过HDMI线直接连接到BLIKVM PCIe卡的HDMI IN接口。HDMI EDID模拟器不是必须要是用的，当您的计算机不能正确输出HDMI画面时，可以通过尝试使用此模块接在你的计算机的HDMI接口上，从而让您的计算机可以输出一个正确扽HDMI画面"
    ![Connect_HDMI_cable_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_1.jpg){width="300"}
    ![Connect_HDMI_cable_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_2.jpg){width="300"}
    ![Connect_HDMI_cable_3](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_HDMI_cable_3.jpg){width="300"}

## **6.连接网线**
!!! note "标准: IEEE 802.3af PoE输入电压:37v-57v."
    ![Connect_the_network_cable](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_the_network_cable.jpg){width="400"}

!!! warning "当使用PoE供电时，不需要使用PWR-IN端口再供电"

## **7.连接USB供电接口**

![Connect_PWR-IN](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Connect_PWR-IN.jpg){width="400"}

!!! warning "当使用PoE供电时, 通过使用PWR-IN端口进行供电的USB电源适配器需要5V/3A。"

## **8.测试**

!!! note "OLED显示屏现实设备IP地址和其它信息"
    ![find_IP](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/find_IP.jpg){width="300"}
    ![test_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/test_all.jpg){width="300"}
    使用该IP地址在浏览器上直接输入，即可打开web控制界面。如果视频鼠标键盘以及其它你关心的功能测试一切正在，就可以将BLIKVM PCIe卡安装到你的机箱中。

## **9.安装BLIKVM PCIe卡到机箱中**

!!! note "断开电源和连接线，先将PCIe卡安装到主板上，然后重新将线缆连接好。不同批次收到的ATX线颜色可能不一样，请直接参考引脚定义进行连接。"
    ![blikvm_in_case](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/blikvm_in_case.jpg){width="300"}
    ![OLED_display_out](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/OLED_display_out.jpg){width="300"}
    ![finish_installation_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/finish_installation_1.jpg){width="300"}
    ![finish_installation_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/finish_installation_2.jpg){width="300"}

到这里你就可以享受BLIKVM PCIe卡来管理你的计算机啦!

## **附录 1.安装半高的PCIe挡板**
!!! note
    ![remove_standard_bracket](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/remove_standard_bracket.jpg){width="300"}
    ![replace_low_bracket_1_1](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_1_1.jpg){width="300"}
    ![replace_low_bracket_2](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_2.jpg){width="300"}
    ![replace_low_bracket_3](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_3.jpg){width="300"}
    ![replace_low_bracket_4](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/replace_low_bracket_4.jpg){width="300"}

## **附录 2.安装散热风扇**

!!! note "通常使用金属散热片已经足够，安装散热风扇不是必须的"
    ![install_fan_prepare](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_prepare.jpg){width="300"}
    ![install_fan_unscrew](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_unscrew.jpg){width="300"}
    ![place_4_nylon_spacers](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/place_4_nylon_spacers.jpg){width="300"}
    ![install_fan_ok](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_ok.jpg){width="300"}
    ![fan_power_polarity](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/fan_power_polarity.jpg){width="300"}
    ![install_fan_all](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/install_fan_all.jpg){width="300"}  

!!! info "风扇被树莓派的GPIO12口控制"

## **附录 3.安装wifi天线**
!!! note
    ![Install_wifi_antenna_prepare](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_wifi_antenna_prepare.jpg){width="300"}
    ![Install_wifi_antenna](assets/images/BLIKVM-PCIe/BLIKVM_PCIe_Installation_Guide.assets/Install_wifi_antenna.jpg){width="300"}
