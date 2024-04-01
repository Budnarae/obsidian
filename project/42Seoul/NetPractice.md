
---

#42Seoul #network 

**

---

#### lv1

![[NetPractice_lv1_before.png]]

1. A1과 D1의 IP 주소가 잘못되었다. IP 주소의 각 옥텟은 255를 넘을 수 없다.
2. A1과 B1, C1과 D1의 네트워크 주소 부분이 서로 일치하지 않는다.

#### lv2

![[NetPractice_lv2_before.png]]

1. A1과 B1의 서브넷 마스크, 네트워크 주소가 서로 일치하지 않는다.
2. C1과 D1 : 127은 스스로를 가리키는 특수 IP 주소이기 때문에 서로 통신하는 데 사용할 수 없다.

![[NetPractice_lv2_after.png]]

#### lv3

![[NetPractice_lv3_before.png]]

1. 같은 LAN 안의 IP 주소는 네트워크 주소와 서브넷 마스크가 모두 일치해야 한다.

![[NetPractice_lv3_after.png]]

#### lv4

![[NetPractice_lv4_before.png]]

1. 라우터 인텊같은 LAN 안의 IP 주소는 네트워크 주소와 서브넷 마스크가 모두 일치해야 한다.