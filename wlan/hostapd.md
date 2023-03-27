# hostapd

## 0. 概述

### 0.1 概念

#### Wi-Fi与IEEE

| 世代名称 | IEEE标准 | 最大速率(Mbps) | 上市年份 | 频率(GHz) |
| -- | -- | -- | -- | -- |
| Wi‑Fi 7 | 802.11be | 1376～46120 | (2024) | 2.4/5/6 |
| Wi‑Fi 6E | 802.11ax | 574～9608 | 2020 | 6 |
| Wi‑Fi 6 | 802.11ax | 574～9608 | 2019 | 2.4/5 |
| Wi‑Fi 5 | 802.11ac | 433～6933 | 2014 | 5 |
| Wi‑Fi 4 | 802.11n | 72～600 | 2008 | 2.4/5 |

#### 基本概念

* `MCS`: 调制编码方案(Modulation Coding Scheme)
* `QAM`: 正交幅度调制模式(Quadrature Amplitude Modulation)

#### 物理层协议

| IEEE标准 | 物理层协议 |
| -- | :--: |
| 802.11ax | HE |
| 802.11ac | VHT |
| 802.11n | HT |

### 0.2 常用命令

* `iw phy`: 查看无线网卡详细参数
* `iw dev wlan0 scan`: 无线网卡`wlan0`扫描热点世代名称[注 1]	IEEE标准	最大速率

* `iw wlan0 info`: 查看无线网卡当前运行情况
* `iw reg get`: 获取当前国家码和非授权频率范围
* `iw reg set CN`: 设置当前国家码为`CN`

## 1. 参考配置

```conf
interface=wlan0
bridge=br-lan
driver=nl80211

ssid=[热点名]
utf8_ssid=1
hw_mode=a
channel=36

ieee80211w=1
wpa=2
wpa_passphrase=[密码]
wpa_key_mgmt=WPA-PSK WPA-PSK-SHA256 SAE
wpa_pairwise=CCMP
auth_algs=1
macaddr_acl=0

ieee80211h=1

ieee80211d=1
country_code=CN

ieee80211n=1
wmm_enabled=1
ht_capab=[HT40+][SHORT-GI-20][SHORT-GI-40][TX-STBC][MAX-AMSDU-7935][DSSS_CCK-40]

ieee80211ac=1
vht_capab=[MAX-MPDU-11454][RXLDPC][VHT160][SHORT-GI-80][SHORT-GI-160][TX-STBC-2BY1][RX-STBC-1][SU-BEAMFORMER][SU-BEAMFORMEE][MAX-A-MPDU-LEN-EXP3][RX-ANTENNA-PATTERN][TX-ANTENNA-PATTERN]
vht_oper_chwidth=2
vht_oper_centr_freq_seg0_idx=50
use_sta_nsts=1

ieee80211ax=1
he_su_beamformer=1
he_su_beamformee=1
he_mu_beamformer=1
he_bss_color=8
he_oper_chwidth=2
he_oper_centr_freq_seg0_idx=50
he_basic_mcs_nss_set=2
```
