# hostapd

## 0. 概述

### 0.1 概念

#### Wi-Fi与IEEE

| 世代名称 | IEEE标准 | 上市年份 | 频率(GHz) |
| -------- | -------- | -------- | --------- |
| Wi‑Fi 7  | 802.11be | (2024)   | 2.4/5/6   |
| Wi‑Fi 6E | 802.11ax | 2020     | 6         |
| Wi‑Fi 6  | 802.11ax | 2019     | 2.4/5     |
| Wi‑Fi 5  | 802.11ac | 2014     | 5         |
| Wi‑Fi 4  | 802.11n  | 2008     | 2.4/5     |

#### 基本概念

* `MCS`: 调制编码方案(**M**odulation **C**oding **S**cheme)
* `QAM`: 正交幅度调制(**Q**uadrature **A**mplitude **M**odulation)
* `GI`: 防护间隔(**G**uard **I**nterval)
* `Symbol`: 符号
* `空间流数`(Spatial Streams): 发送和接收数据天线数量

#### 物理层协议

| IEEE标准 | 物理层协议 |
| -------- | :--------: |
| 802.11ax |     HE     |
| 802.11ac |    VHT     |
| 802.11n  |     HT     |

#### 复用

* `FDM`: 频分多路复用(**F**requency **D**ivision **M**ultiplexing)
* `OFDM`: 正交频分复用(**O**rthogonal **F**requency **D**ivision **M**ultiplexing)
* `FDMA`: 频分多址(**F**requency **D**ivision **M**ultiple **A**ccess)
* `OFDMA`: 正交频分多址(**O**rthogonal **F**requency **D**ivision **M**ultiple **A**ccess)

```plantuml
@startmindmap
* OFDMA
** FDMA
** OFDM
*** FDM
@endmindmap
```

FDM vs OFDM:

![1](https://www.researchgate.net/profile/Ufuk-Tamer/publication/346403990/figure/fig2/AS:962578058588160@1606507901355/Spectrum-Usage-OFDM-vs-FDM-21.ppm)

OFDM vs OFDMA:

![2](https://miro.medium.com/v2/resize:fit:1400/0*aQFX9fRJY_OaCouE)

| IEEE标准 | 最小子载波频率(kHz) | 20MHz数据子载波数 | 40MHz数据子载波数 | 80MHz数据子载波数 | 160MHz数据子载波数 |
| -------- | :-----------------: | :---------------: | :---------------: | :---------------: | :----------------: |
| 802.11ax |       78.125        |        234        |        468        |        980        |       2x980        |
| 802.11ac |        312.5        |        52         |        108        |        234        |         -          | - |
| 802.11n  |        312.5        |        52         |        108        |         -         |         -          | - |

#### 传输速率

$$
理论传输速率=空间流数\times\frac{1}{𝑆𝑦𝑚𝑏𝑜𝑙传输时长+𝐺𝐼}\times𝑆𝑦𝑚𝑏𝑜𝑙二进制长度\times编码率\times数据子载波数
$$

由于计算过于麻烦，所以一般直接查[调制编码方案表](https://en.wikipedia.org/wiki/Wi-Fi_6#cite_note-17)可以直接得到单空间流的速率。

<table>
<caption>调制编码方案
</caption>
<tbody><tr>
<th rowspan="3">MCS<br>index
</th>
<th rowspan="3">Modulation<br>type
</th>
<th rowspan="3">Coding<br>rate
</th>
<th colspan="8">Data rate (Mbit/s)
</th></tr>
<tr>
<th colspan="2">20&nbsp;MHz channels</th>
<th colspan="2">40&nbsp;MHz channels</th>
<th colspan="2">80&nbsp;MHz channels</th>
<th colspan="2">160&nbsp;MHz channels
</th></tr>
<tr>
<th>1600&nbsp;ns GI</th>
<th>800&nbsp;ns GI</th>
<th>1600&nbsp;ns GI</th>
<th>800&nbsp;ns GI</th>
<th>1600&nbsp;ns GI</th>
<th>800 ns GI</th>
<th>1600&nbsp;ns GI</th>
<th>800 ns GI
</th></tr>
<tr>
<td>0</td>
<td>BPSK</td>
<td>1/2</td>
<td>8</td>
<td>8.6</td>
<td>16</td>
<td>17.2</td>
<td>34</td>
<td>36.0</td>
<td>68</td>
<td>72
</td></tr>
<tr>
<td>1</td>
<td>QPSK</td>
<td>1/2</td>
<td>16</td>
<td>17.2</td>
<td>33</td>
<td>34.4</td>
<td>68</td>
<td>72.1</td>
<td>136</td>
<td>144
</td></tr>
<tr>
<td>2</td>
<td>QPSK</td>
<td>3/4</td>
<td>24</td>
<td>25.8</td>
<td>49</td>
<td>51.6</td>
<td>102</td>
<td>108.1</td>
<td>204</td>
<td>216
</td></tr>
<tr>
<td>3</td>
<td>16-QAM</td>
<td>1/2</td>
<td>33</td>
<td>34.4</td>
<td>65</td>
<td>68.8</td>
<td>136</td>
<td>144.1</td>
<td>272</td>
<td>282
</td></tr>
<tr>
<td>4</td>
<td>16-QAM</td>
<td>3/4</td>
<td>49</td>
<td>51.6</td>
<td>98</td>
<td>103.2</td>
<td>204</td>
<td>216.2</td>
<td>408</td>
<td>432
</td></tr>
<tr>
<td>5</td>
<td>64-QAM</td>
<td>2/3</td>
<td>65</td>
<td>68.8</td>
<td>130</td>
<td>137.6</td>
<td>272</td>
<td>288.2</td>
<td>544</td>
<td>576
</td></tr>
<tr>
<td>6</td>
<td>64-QAM</td>
<td>3/4</td>
<td>73</td>
<td>77.4</td>
<td>146</td>
<td>154.9</td>
<td>306</td>
<td>324.4</td>
<td>613</td>
<td>649
</td></tr>
<tr>
<td>7</td>
<td>64-QAM</td>
<td>5/6</td>
<td>81</td>
<td>86.0</td>
<td>163</td>
<td>172.1</td>
<td>340</td>
<td>360.3</td>
<td>681</td>
<td>721
</td></tr>
<tr>
<td>8</td>
<td>256-QAM</td>
<td>3/4</td>
<td>98</td>
<td>103.2</td>
<td>195</td>
<td>206.5</td>
<td>408</td>
<td>432.4</td>
<td>817</td>
<td>865
</td></tr>
<tr>
<td>9</td>
<td>256-QAM</td>
<td>5/6</td>
<td>108</td>
<td>114.7</td>
<td>217</td>
<td>229.4</td>
<td>453</td>
<td>480.4</td>
<td>907</td>
<td>961
</td></tr>
<tr>
<td>10</td>
<td>1024-QAM</td>
<td>3/4</td>
<td>122</td>
<td>129.0</td>
<td>244</td>
<td>258.1</td>
<td>510</td>
<td>540.4</td>
<td>1021</td>
<td>1081
</td></tr>
<tr>
<td>11</td>
<td>1024-QAM</td>
<td>5/6</td>
<td>135</td>
<td>143.4</td>
<td>271</td>
<td>286.8</td>
<td>567</td>
<td>600.5</td>
<td>1134</td>
<td>1201
</td></tr></tbody></table>

### 0.2 常用命令

* `iw phy`: 查看无线网卡详细参数
* `iw dev wlan0 scan`: 无线网卡`wlan0`扫描热点
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
ht_capab=[LDPC][HT40+][SHORT-GI-20][SHORT-GI-40][TX-STBC][RX-STBC1][MAX-AMSDU-7935][DSSS_CCK-40]

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
