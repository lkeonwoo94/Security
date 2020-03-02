# Security
정보보안에 대해 학습합니다.
---

**Software Vunerability**
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





---
reference
* [해커의관점에서 바라보기 Naver D2 2018](https://www.slideshare.net/deview/131-119007645)
