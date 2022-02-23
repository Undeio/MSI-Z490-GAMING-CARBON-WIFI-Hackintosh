# MSI-Z490-Gaming-Carbon-WIFI-Hackintosh

## 更新说明

1. 官方文档更新，修改机型为`iMac20,2`，[官方说明](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#platforminfo)；
2. 同步修改 USB 定制，改为通用定制（`UTBMap.kext`），不再涉及机型信息，但需要配合`USBToolBox.kext`使用；
3. 添加`SSDT-SBUS-MCHC.aml`，防止出现睡眠问题，[官方说明](https://dortania.github.io/OpenCore-Post-Install/universal/sleep.html#smbus)；
4. 当前配置日常稳定使用，已关闭啰嗦模式，初次安装请执行以下操作：
   1. 替换 EFI/BOOT/BOOTx64.efi 为 DEBUG 版本；
   2. 替换 EFI/OC/Drivers/OpenRuntime.efi 为 DEBUG 版本；
   3. 替换 EFI/OC/OpenCore.efi 为 DEBUG 版本；
   4. 启用 Misc 设置中 Debug 选项下的 AppleDebug；
   5. 请将 Misc 设置中 Debug 选项下的 Target 设置为 67；
   6. 请在 NVRAM 设置中 Add 选项下`7C436110-AB2A-4BBB-A880-FE41995C9F82`条目的 boot-args 中添加 -v 参数；

## 配置说明

### 重要提示 - 必须做的

配置文件无法开箱即用，使用前请先修改`PlatformInfo`下的机型信息：

配置文件无法开箱即用，使用前请先修改`PlatformInfo`下的机型信息：

配置文件无法开箱即用，使用前请先修改`PlatformInfo`下的机型信息：

### 机器配置

|   硬件   |                     型号                     |         备注         |
| :------: | :------------------------------------------: | :------------------: |
|   机箱   |                 机械大师 C34                 |       真的很小       |
|   主板   |         MSI Z490 GAMING CARBON WIFI          |         ATX          |
|   BIOS   |                     1.A0                     |      2021-09-30      |
|   CPU    |               Intel i9-10850K                | 个人感觉比 10900K 香 |
|   内存   |           英睿达铂胜 D4 3600 16Gx4           |     准备转投 PVE     |
|   磁盘   |                 铠侠 RD10 1T                 |                      |
|   声卡   |               Realtek ALC1220P               | VEN_10EC & DEV_1168  |
| 有线网卡 |               Realtek RTL8125B               | VEN_10EC & DEV_8125  |
| 无线网卡 |                 Intel AX201                  |      BIOS 禁用       |
| 无线网卡 |                  BCM94360Z3                  |                      |
|   蓝牙   |                   同上 👆                    |                      |
|   显卡   | 昂达 RX560 典藏版，说白了就是国内特供版 560D |  太穷，只配用亮机卡  |
|  显示器  |                 三星 C24F390                 |         HDMI         |

### 详细信息

- OC 版本：0.78；
- Wi-Fi，蓝牙，随航，隔空投送正常；
- 开关机，睡眠，唤醒正常(测试时间较短，仅供参考)；

  唤醒说明：平时使用误触键盘或鼠标总会无端唤醒，所以这里仅支持按下电源键唤醒；

- HDMI / DP 显示正常（单显示）；
- 音频输出正常（麦克风未测试）；
- USB 测试正常；

  USB 定制说明：由于 15 端口限制，有线网卡左侧的两个 USB3.0 端口仅支持 3.0；

  示意图：
  ![USB 定制](https://tva1.sinaimg.cn/large/008i3skNly1gzdczpkwsyj30t40q8ac9.jpg)

- OC 主题 `AppleSilicon`，来自 [heipg.cn](https://heipg.cn)；
