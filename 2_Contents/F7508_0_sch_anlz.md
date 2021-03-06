# 
## 0. STM32F7508-Discovery kit 하드웨어 분석 
 ### [목차로 돌아가기](https://github.com/d-h-k/STM32F7508#%EB%AA%A9%EC%B0%A8-index)
 > 이 문서에서는 [STM32F7508-Discovery kit](https://www.st.com/en/evaluation-tools/stm32f7508-dk.html) 학습을 위한 기본적인 하드웨어 이해에 대하여 다룹니다
  ```
  - 이 글에서는 ST에서 제공하는 회로도를 기준으로 분석합니다
  - 동일한 하드웨어에 대하여 다양한 관점이 있을수 있습니다
  ```
  - [STM32F7508-Discovery kit](https://www.st.com/en/evaluation-tools/stm32f7508-dk.html)는 제공되는 파일로 보아 Altium이 사용되었으나 이 글에서는 Altium을 사용하지 않습니다
  - [여기를 클릭하여](https://www.st.com/en/evaluation-tools/stm32f7508-dk.html#resource)ST 사이트에 접속하여 회로도와 각종 자료를 다운로드 합니다
  - 제가 사용하는 ST제공 자료들을 다운받기 위해서는 [여기를 클릭합니다](../0_materials_ST) 
  - 이번 글에서 사용하는 CubeMX프로젝트는 기본으로 설정되는 값을 기준으로 합니다. 초반의 CubeMX설정에 대하여 궁금하신 분들은 [1번 문서를 참고 해 주시기 바랍니다]()
  - cubeMX에서의 Pin Config Map 입니다
    - ![sd](../img/20190713-001.jpg) 
  - GPIO 셋팅 부분 입니다
    - ![sd](../img/20190713-002.jpg) 
  - LCD 컨트롤러 부분입니다
    - ![sd](../img/20190713-003.jpg) 
  - 타이머 1 부분 설정
    - ![sd](../img/20190713-004.jpg) 
  - 타이머 2 부분 설정
    - ![sd](../img/20190713-005.jpg) 
  - 타이머 3 부분 설정
    - ![sd](../img/20190713-006.jpg) 
  - UART부분
    - ![sd](../img/20190713-007.jpg) 
  - USB 
    - ![sd](../img/20190713-008.jpg) 
  - Flash 메모리 부분입니다. SPI 통신 방식 사용
    - ![sd](../img/20190713-009.jpg) 
  - SD 메모리 카드 부분입니다
  - 이부분은 Fat Filesystem 라이브러리를 사용합니다
  - Fat Filesystem 에 대하여 추후에 추가 보충자료를 제공 예정입니다
    - ![sd](../img/20190713-010.jpg) 
  - ADC부분 입니다 아두이노 호환 커넥터에 연결 되어 있습니다
    - ![sd](../img/20190713-011.jpg) 
  - 메모리 컨트롤러 입니다. 이 보드에는 SDRAM이 장착되어 있으며 16비트 모드로 동작합니다 이 부분은 아래 회로도에서 확인해 보겠습니다
    - ![sd](../img/20190713-012.jpg) 
  - GFX 설정 부분입니다 - 1
    - ![sd](../img/20190713-014.jpg) 
  - GFX 설정 부분입니다 - 2
    - ![sd](../img/20190713-015.jpg) 
  - GFX 설정 부분입니다 - 3
    - ![sd](../img/20190713-016.jpg) 
  - 클럭 설정 부분입니다 Main 클럭이 200Mhz로 동작합니다
    - ![sd](../img/20190713-017.jpg) 
  - 회로도의 전체 프로젝트 회로도입니다.
  - 개인적으로 Altium에서 가장 좋아하는 기능인데요, 전체적으로 어떤 모듈과 어떻게 연결되어 있는지 확인할 수 있습니다.
  - 해당 보드에서는 모든 기능과 주변회로들이 MCU만을 바라보는 회로입니다. 
    - ![sd](../img/20190713-018.jpg) 
  - 여기서 추가적인 하드웨어 모듈을 위해서 마련된 아두이노 우노 호환 핀헤더의 모습입니다. 아래에서 해당 부분의 회로도를 자세히 살펴보겠습니다
    - ![sd](../img/20190713-019.jpg) 
  - 이제 너무나도 친근하게 느껴지는 STM32F103C8T6이 ST-Link역할을 위해 위치합니다.
  - 이제보니 STM32F103C8T6의 엄청난 가성비는 ST에서 팔려고 만든게 아니라 자기들이 쓰려고 만든 느낌마져.. 드네요
  - STM32 패밀리 사상 최고의 리테일용 베스트 아이템 아닐까 생각합니다.
    - ![sd](../img/20190713-020.jpg) 
  - ST 링크 주변의 파워 토폴로지 부품
    - ![sd](../img/20190713-021.jpg) 
  - SAI 를 위한 오디오 인터페이스 코덱 모듈입니다 - STM32F746디스커버리 보드와 매우매우 유사하네요..
    - ![sd](../img/20190713-022.jpg) 
  - QuadSPI 플레쉬 메모리 모듈입니다
  - SPI 통신으로 Nand Flash 를 읽고 쓰는데, CLK+CS핀으로 제어라며 데이터는 4비트씩 읽어옵니다 - STM32F746디스커버리 보드와 매우매우 유사하네요.. 전반적으로 유사합니다...!
    - ![sd](../img/20190713-023.jpg) 
  - 여기에 아두이노 우노 커넥터가 존재합니다
  - 여기서 우노 커넥터에 연결된 User Control Pin들을 확인할 수 있습니다
    - ![sd](../img/20190713-024.jpg) 
  - SDRAM입니다 Nand Flash와는 다르게 Data BUS + Address BUS가 존재합니다
  - (다들 저보다 잘 아시겠지만..) 메모리는 Byte단위 엑세스와 Random Access가 가능하므로 여기서 코드의 실행이 가능합니다
    - ![sd](../img/20190713-025.jpg) 
  - USB 통신을 위한 부분입니다.
  - 여기서 DM신호선과 DP신호선은 Differential pole pair 신호선 설정이 되어 있는데 마치 CAN의 그것처럼 두 신호의 임피던스를 매칭해야 한다는 표기입니다. 
    - ![sd](../img/20190713-026.jpg) 
  - 이상으로 간단하게 하드웨어 리뷰 및 설명을 마치겠습니다.
  - 부족한 글 끝가지 읽어 주셔서 감사합니다
