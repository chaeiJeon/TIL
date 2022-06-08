beforeunload 이벤트는 문서와 그 리소스가 언로드 되기 직전에 window에서 발생한다.

- 이벤트 발생 시점엔 문서를 아직 볼 수 있으며 이벤트 취소도 가능하다.

- beforeunload 이벤트를 사용하면 사용자가 페이지를 떠날 때 정말로 떠날 것인지 묻는 확인 대화 상자를 표시할 수 있다. 

- 확인을 누르면 새로운 페이지로 탐색하고, 취소할 경우 현재 페이지에 머문다.

- 현재 대부분의 브라우저에서는 사용자 지정 문구를 사용하지 않으며 이 동작을 지원하지 않는다.

- 이벤트 처리 중에는 window.alert(), window.confirm(), window.prompt() 메서드를 무시할 수 있다.




자재를 등록할 때 입력하다가 중간에 뒤로가기 버튼을 누르면 경고창 없이 그냥 이동되어 버린다. 이 문제를 해결하기 위해 beforeunload 이벤트를 사용하였다.

window.addEventListener("beforeunload", (event) => {
  event.preventDefault();
  event.returnValue = "";
});