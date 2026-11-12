
# purpose
언리얼 엔진의 메모리 할당자 중 하나인 FMallocBinned3 에 대한 설명과 구현을 다룹니다.

# Analysis Environment
Windows
UE 5.8.1

--- 

# Memory Allocator
메모리 할당자를 만들때 주의할 점은 다음과 같다.

### OS API
OS API를 통해 가상주소를 예약(Reserve), 커밋(Commit), 해제(Release) 한다.
예약은 64kib 단위로, 커밋과 커밋 해제는 페이지 단위로 정렬된다. 
호출 비용이 큼으로 자주 호출하지 않아야 한다.

### Fragmentation
메모리 할당자는 os로부터 할당 받은 메모리를 낭비 없이 제공해야한다.

정렬된 크기를 제공해야함으로 크기가 다른 메모리를 나란히 제공하였다면  
빈 공간이 만들어지는 Internal Fragmentation 문제가 발생한다.

연속된 메모리를 요구 받았을 경우 이미 할당된 메모리가 중간에 끼어있다면 
전체 메모리는 충분하지만 제공하지 못하는 External Fragmentation 문제가 발생한다.

### Race Condition
메모리 할당과 반환은 스레드 안전성을 보장해야 한다.
동기화는 성능을 갉아먹는 주범이다.

---

# FMallocBinned3

요구된 크기에 따라 큰 할당과 작은 할당을 구분한다.




큰 할당의 경우 미리 가상 주소를 예약하는 것이 


### bin

가상 주소는 bin 별로 구역을 나눈다.



