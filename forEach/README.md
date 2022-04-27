forEach에서 return을 하는 것은 forEach 메소드에 콜백 함수를 전달하는 것이다.

forEach에서 루프를 진행하는데 있어 return은 아무런 영향을 미치지 않는다.

* MDN 공식 문서의 forEach에 관한 설명
예외를 발생시키는 경우를 제외하고는 forEach() 루프를 중단시킬 방법은 없다.
만약 그러한 목적으로 forEach() 메소드를 사용하는 것은 잘못된 방법이다.

=> for문을 사용한다
ex) for(let value of array)
