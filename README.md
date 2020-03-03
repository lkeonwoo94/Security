# Security
정보보안에 대해 학습합니다.
---

**Software Vulnerability**
```
+ Native system -- Reverse Engineering
|               +- Memory corruption -  stack buffer overflow
|                                    +- heap buffer overflow
|                                    +- Use-after-free(UAF)        - 해제된 메모리 영역을 ref `*p` 로 사용할 때 발생
|                                    +- 메모리유출                  - 개발자가 의도한 양보다 많은 양을 출력
|================================================================================================================
+ Web ----------- Client--------------- XSS                        - ex. script doc.cookie
                |                    +- CSRF                       - ex. a href tag
                |
                +- Server-------------  Directory Indexing
                                     +- File download & upload
                                     +- SQL injection 
                                     +- DoS
                                     +- Docker, Container ..
```
```
=> Secure coding guide line / Static analysis tool
```

**Hardware Vulnerability**
```
* 디버깅 포트/핀을 이용한 펌웨어 덤프
  * 가장 쉬운 방법은 UART 시리얼 인터페이스를 통해 얻은 쉘로 파일시스템 복사
  * JTAG를 통해 플래시 메모리 덤프가 가능하긴 하나 ,플래시 종류에 따라 접근 방법이 다름
     * 병렬 NOR Flash 경우, JTAG로 바로 메모리 주소와 길이 설정 후 읽기
     * 직렬 디바이스에 연결된 NOR Flash 경우, SPI 컨트롤러 통해 통신
     * NAND나 eMMC의 경우 알맞은 컨트롤러와 통신
  * 덤프를 뜬 펌웨이 이미분석 툴 : [Binwalk](https://github.com/ReFirmLabs/binwalk)
  * 보통은 파일시스템 또는 리눅스 커널 이미지
    * 커널이미지라면 ramdisk 덤프!
* Fault injection공격
   * 전류를 흘려보내어 특정bit를 뒤집거나 코드 실행 흐름을 변경
* 사이드채널공격
   * 전류 흐름과 사용량을 감지하여 암호 알고리즘 키 도출
```




---
reference
* [해커의관점에서 바라보기 Naver D2 2018](https://www.slideshare.net/deview/131-119007645)

---

구글해킹 : intitle 관리자 페이지 inurl /admin/ (이거 왜쳤더라 .. 나중에 다시)
디렉터리 목록 찾기
intitle:index.of "parent directory"
intitle:index.of name size


admin directory
intitle:index.of.admin
intitle:index.of inurl:admin

서버 버전 확인
intitle:index.of "server at"

특정 서버 버전 찾기
"intitle:index.of "Apache/1.3.27 Server at" 등

백업 파일 탐색.
> html 페이지는 소스보기를 통해 볼 수 있지만 php등의 서버 스크립트는 그런 방식으로 볼 수 없다.
하지만 사본(백업)을 저장해 두고, 그것을 찾을 수 있다면 소스를 확인해볼 수 있다.

intitle:index.of index.php.bak
inurl:index.php.bak


취약 웹 application 정보들
GHDB : http://www.hackersforcharity.org/ghdb/

error | warning
에러페이지를 찾는다. 이를 통해 서버에 관한 정보들을 조금이나마 건질 수 있다.
etc. "access denied for user" "using password"

login | logon
정문 페이지. 관리자 정보를 습득하고, 사회공학해킹에 이용할 수 있다.
cf. 실제 서버관리자는 다를 경우 whois 등에서 확인할 수 있다.
사실 whois를 이용하는게 훨씬 빠르다. 
기술팀, 관리자, 등록자, 도메인 위치 등을 파악할 수 있다.

username | userid | employee.ID | "your username is"

password | passcode | "your password is"

admin | administrator
admin | administrator "contact your"

-ext:html,htm,shtml,asp,php,aspx
흔히 사용하는 페이지 형식을 제외한 페이지들을 검색

inurl:temp,tmp,backup,bak

intranet | help.desk

filetype:reg intext:"internet account manager"
