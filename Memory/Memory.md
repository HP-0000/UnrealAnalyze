
# purpose
컴퓨터 구조 차원에서 메모리 시스템을 설명합니다.

# Analysis Environment
Windows 64 bit

---

### Storage & Memory
컴퓨터의 HDD 그리고 SSD 는 데이터를 저장한다.
CPU가 가장 빠르게 접근할 수 있는 작업 공간은 RAM 이다.
RAM의 물리 메모리를 4kib 단위로는 프레임이라 부른다.
CPU는 저장 장치의 데이터를 RAM 으로 가져온다.

### Virtual Address
운영체제는 프로세스 단위로 가상 주소 체계를 제공한다.
가상 주소를 4kib 단위로는 페이지라 부른다.
프로세스 단위로 RAM에는 페이지 테이블이 생성되며 
페이지 테이블을 이루는 Page Table Entry 는 할당된 프레임 인덱스가 적혀있다.
가상 주소의 하위 12비트는 페이지 내부의 오프셋을 의미한다.
이어서 36비트는 테이블 시작 주소에서 Page Table Entry 을 탐색하기 위한 오프셋을 나타낸다.

프로세스 내의 스레드들은 가상주소를 공유한다.