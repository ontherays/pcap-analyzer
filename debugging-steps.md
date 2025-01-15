# Debugging Steps

## Problem definition
- The gNB can have E2E. For connected UEs, the throughput is relative low because when iperf3 target bitrate setting higher than 60 Mbits/sec, 
UE will disconnect to gNB

## Purpose of the test.
Verify throughtput as per following Parameter in Integration of OAI gNB(BBU version/branch: develop/commit 68191088a) + JURA RU(SDK v2.2.2) on R750.
:::Info
Number of carriers (J) = 1
Number of layers (ν) = 2
Modulation (Q = 6) = 64QAM
Scaling factor (f) = 1
Band = n78
Sub carrier spacing (μ) = 30 KHz
Bandwidth = 100 MHz
Maximum RB allocation = 273
Overhead = 0.14
Data throughput = 10-6 * 1 * 2 * 6 * 1 * (948/1024) * (273 * 12) * (14 * 21) / 10-3 * (1 - 0.14) = *876.4 Mbps*
:::

## Test 1:

### Test configuration: 
- Configure gNB as per gnb.sa.band78.273prb.fhi72.4x4-liteon.conf
- MIMO scheme 4T4R
- slot format- DDDSU
- DUT(UE) Release 15 (Can be checked in UECapabilityinfo)

### Lab tools setup: 
- Turn on MTK tool to capturre logs.
- Install ping-tool to verify throught
-
### Text Prrocedure:
1. Turn on the flight mode.
2. Turn Off the flight mode. 
3. Device attaches to cell n78.
4. PDU session establish.
5. Verify Device has internet access.
6. Verify network icon shows '5G'.
7. From server send `iperf3 -s <server ip> -p <port_no>`
        <iperf3 -s 192.168.8.21 -p 5201>
8. From UE iperf tool send (udp) `iperf3 -u -c <server_IP> -b <target_bitrate> -t <duration> -i <interval> -l <packet_size> -p <port_number>`
<iperf3 -u -c 192.168.8.21 -b <80> -t 30 -i 5 -l 1300 -p 5201>
9. UE(DUT) able to receive data.
10. DUT(UE) stop receiving data and UE context released.

### Result:
| Parameters | Expected  | Actual |
| :----: | :---: | :-------: |
| Throughput       |       |         |
|        |       |          |


## Test 2.

## Test configuration: 
- Configure gNB as per gnb.sa.band78.273prb.fhi72.4x4-liteon.conf
- MIMO Scheme 2T2R

## Lab tools setup: 
- Turn on MTK tool to capturre logs.
- Install ping-tool to verify throught

### Text Procedure:
1. Turn on the flight mode.
2. Turn Off the flight mode. 
3. Device attaches to cell n78.
4. PDU session establish.
5. Verify Device has internet access.
6. Verify network icon shows '5G' (in Idle mode).
7. From server send <iperf3 -s 192.168.8.21 -p 5201>
8. From UE iperf tool send <iperf3 -u -c 192.168.8.21 -b <80> 100-t 30 -i 5 -l 1300 -p 5201.

### Result:
| Parameters | Expected  | Actual |
| :----: | :---: | :-------: |
| Throughput       |       |         |
|        |       |          |

## Test 3.

### Test configuration: 
- Configure gNB as per gnb.sa.band78.273prb.fhi72.4x4-liteon.conf
- MIMO Scheme 2T2R

### Lab tools setup: 
- Turn on MTK tool to capturre logs.
- Install ping-tool to verify throught

### Text Procedure:
1. Turn on the flight mode.
2. Turn Off the flight mode. 
3. Device attaches to cell n78.
4. PDU session establish.
5. Verify Device has internet access.
6. Verify network icon shows '5G' (in Idle mode).
7. From server send <iperf3 -s 192.168.8.21 -p 5201>
8. From UE iperf tool send <iperf3 -u -c 192.168.8.21 -b <100> 100-t 30 -i 5 -l 1300 -p 5201.

### Result:
| Parameters | Expected  | Actual |
| :----: | :---: | :-------: |
|  Throughtput      |       |         |
|        |       |          |
