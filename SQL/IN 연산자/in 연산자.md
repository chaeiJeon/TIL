코딩테스트 연습 > 루시와 엘라 찾기

​

처음엔 sql문 작성을 다음과 같이 하였다.

SELECT
animal_id, name, sex_upon_intake
from animal_ins
where name='Lucy' OR name='Ella' OR name='Pickle' OR name='Rogan' OR name='Sabrina' OR name='Mitty'
order by animal_id;
더 효율적으로 작성할 방법이 있을 것 같아 찾아본 결과 IN 연산자​를 사용하면 된다고 한다.

​

​

​

IN 연산자

WHERE 절 내에서 특정값 여러개를 선택하는 연산자

괄호 내의 값 중 일치하는 것이 있으면 TRUE

​

​

IN 연산자를 사용하면 다음과 같이 query를 바꿀 수 있다. 길이도 짧아지고 훨씬 간단해졌다.

SELECT
animal_id, name, sex_upon_intake
from animal_ins
where name IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
order by animal_id;
​