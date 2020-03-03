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
