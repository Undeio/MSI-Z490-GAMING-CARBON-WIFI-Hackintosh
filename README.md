# MSI-Z490-Gaming-Carbon-WIFI-Hackintosh

## 更新说明

### New's

---

1. 更新 OC 至 0.79；
2. 更新设置，以使 Windows 下可以正确识别机型；

   1. Kernel / Quicks / CustomSMBIOSGuid : `Enable`;
   2. Platforminfo / Generic / SpoofVendor :` Enable`;
   3. Platforminfo / UpdateSMBIOSMode : `Custom`;
   4. 同时修改系统 UUID 为 Windows 系统中显示的 UUID，防止出现 Windows 激活失败问题（已发生并修复）；
   5. 要查看 Windows 下的系统 UUID，请在系统管理员权限 CMD 窗口下依次执行如下命令：

      ```powershell
      wmic

      csproduct # 或者 csproduct list full
      ```

3. 不再尝试修复由 macOS 切换至 Windows 产生的蓝屏问题，得不偿失，现在直接使用 Windows 原生引导启动；
   1. BIOS 启动选择快捷键 F11；
   2. Windows 直接选择硬盘原生启动；
   3. macOS 依旧使用 OC 引导启动；

### Old's

---

1. 官方文档更新，修改机型为`iMac20,2`，[官方说明](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#platforminfo)；
2. 同步修改 USB 定制，改为通用定制（`UTBMap.kext`），不再涉及机型信息，但需要配合`USBToolBox.kext`使用；
3. 添加`SSDT-SBUS-MCHC.aml`，防止出现睡眠问题，[官方说明](https://dortania.github.io/OpenCore-Post-Install/universal/sleep.html#smbus)；
4. 在系统报告中添加网卡 / USB 控制器等常用 PCI 设备；
5. 当前配置日常稳定使用，已关闭啰嗦模式，初次安装请执行以下操作：
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
|   机箱   |                 机械大师 C34                 | 堪比 ITX 的 ATX 机箱 |
|   主板   |         MSI Z490 GAMING CARBON WIFI          |         ATX          |
|   BIOS   |                 E7C73IMS.1A0                 |      2021-10-18      |
|   CPU    |               Intel i9-10850K                | 个人感觉比 10900K 香 |
|   内存   |           英睿达铂胜 D4 3600 16Gx4           |   未来可能会用 PVE   |
|   磁盘   |                 铠侠 RD10 1T                 |                      |
|   声卡   |               Realtek ALC1220A               | VEN_10EC & DEV_1168  |
| 有线网卡 |               Realtek RTL8125B               | VEN_10EC & DEV_8125  |
| 无线网卡 |                 Intel AX201                  |      BIOS 禁用       |
| 无线网卡 |                  BCM94360Z3                  |                      |
|   蓝牙   |                   同上 👆                    |                      |
|   显卡   | 昂达 RX560 典藏版，说白了就是国内特供版 560D |   亮机卡，原生免驱   |
|  显示器  |                 三星 C24F390                 |         HDMI         |

### 详细信息

- Wi-Fi，蓝牙，随航，隔空投送正常；
- 开关机，睡眠，唤醒正常；

  唤醒说明：平时使用误触键盘或鼠标总会无端唤醒，所以这里仅支持按下电源键唤醒；

- HDMI / DP 显示正常（单显示 ｜ 双显示 ｜ 热拔插）；
- 音频输出正常（麦克风未测试）；
- USB 测试正常；

  USB 定制说明：由于 15 端口限制，有线网卡左侧的两个 USB3.0 端口仅支持 3.0；

  示意图：
  ![USB 定制](https://tva1.sinaimg.cn/large/008i3skNly1gzdczpkwsyj30t40q8ac9.jpg)

- OC 主题 `AppleSilicon`，来自 [heipg.cn](https://heipg.cn)；
