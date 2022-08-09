보호소에 들어온 동물의 정보를 담은 테이블 animal_ins, 

보호소에서 입양 보낸 동물의 정보를 담은 테이블 animal_outs, 라 한다

사고가 발생하여 animal_outs에 A 동물의 정보가 있는데 animal_ins에는 해당 동물의 정보가 유실되어 버렸다.

이 유실된 정보를 모두 출력하는 것이 문제이다.

​

A, B를 right join하고 animal_ins가 null인 것을 가져오도록 조건을 달면 문제가 해결된다.


SELECT aOuts.animal_id, aOuts.name 
   from animal_ins aIns right join animal_outs aOuts 
   on aIns.animal_id = aOuts.animal_id 
   WHERE aIns.animal_id IS NULL;