jquery ajax를 활용하여 화면을 동적으로 깜빡임 없이 이동할 수 있다.

화면을 동적으로 바꾸기 위해서는 dataType을 html로 지정해야 한다.

function setDiyList(res) {
  let dataObject = new Object();
  dataObject = Object.assign({}, res);

  $.ajax({
    url: API_URL + `/REQUEST/postList.php`,
    async: true,
    type: "POST",
    data: {
      data: dataObject,
    },
    dataType: "html",
    cache: false,
  }).done(function (ctx) {
    removeAllChild(diy_list);
    diy_list.innerHTML = ctx;
  });
}
