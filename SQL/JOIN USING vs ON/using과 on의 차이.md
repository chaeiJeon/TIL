USING과 ON은 테이블 JOIN시 사용된다.

​

USING은 두 테이블간 필드 이름이 같은 경우 사용된다.

SELECT i.animal_id, i.name
from animal_ins i
join animal_outs o
    using (animal_id)


ON은 두 테이블간 조인해줘야 하는 필드 이름이 다른 경우 사용된다. 이름이 같은 경우에도 사용할 수 있다.

SELECT i.animal_id, i.name
from animal_ins i
join animal_outs o
    on i.animal_id = o.animal_id
​

​

가져오는 결과에 차이가 있는데 

USING은 같은 필드 이름을 한 번만 가져오는 반면,

ON은 각각의 필드를 가져오기 때문에 중복이 생긴다.

그래서 필드 이름이 같은 경우 USING을 쓰면 데이터 양을 줄일 수 있다.