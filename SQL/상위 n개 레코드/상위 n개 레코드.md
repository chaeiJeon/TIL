원래 n개의 레코드를 가져올 때 다음과 같이 query문을 짜곤 했다.


select name
from animal
order by datetime
limit 1


그런데 어차피 가장 시간이 오래된 데이터 하나만 가져올건데 datetime을 기준으로 모든 데이터를 정렬하고 가장 첫번째 데이터 하나만 가져오는 것이 비효율적이라고 생각해서 다음과 같이 쿼리를 바꾸었다.

​

​

서브쿼리를 사용하여 최소 datetime 값을 구해서, animal 테이블에서 구해진 데이터 값과 일치하는 레코드를 구해오게 하였다.


select name
from animal
where datetime = (select min(datetime) from animal)
