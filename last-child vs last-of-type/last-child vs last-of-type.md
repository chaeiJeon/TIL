# 문제 상황

mmProduct_card > div > mmProduct_model

의 구조로 짜여져 있었음

mmProduct_model 클래스를 가진 마지막 요소에만 아래 마진을 주고 싶었는데 먹지 않았음


//안됨
.mmProduct_card > div > .mmProduct_model:last-child {
  margin-bottom: 8px;
}





# 해결방법

https://css-tricks.com/almanac/selectors/l/last-child/
여기를 찾아보니, last-child는 오직 부모 요소의 가장 마지막 자식만 일치시키려고 하지만,
last-of-type은 마지막으로 끝나지 않더라도 지정된 요소의 마지막 항목과 일치시키게 한다고 되어 있었음



div > mmProduct_model 의 뒤에 div 요소가 하나 더 있어서 9번째 줄처럼 css를 지정했을 때 먹지 않았던 것
왜냐하면 last-child는 무조건 부모 요소의 마지막 자식만 찾으니까



그래서 더 명확하게 찾아주는 last-of-type으로 바꾸었음

//됨
.mmProduct_card > div > .mmProduct_model:last-of-type {
  margin-bottom: 8px;
}

해결!





# 결론

특정 클래스를 가지는 마지막 요소를 찾고 싶을 때는 last-of-type 써야 함