ajax를 통한 php로 배열 전송

- 색인 배열은 그대로 넘겨지지만, 연관 배열은 Object로 넘겨줘야 한다.

// BEFORE (res는 배열)
// js
const ajaxOption = {
    url: API_URL + `/REQUEST/postList.php`,
    async: true,
    type: "POST",
    data: {
        "data": res,
    },
    dataType: "html",
    cache: false,
    };
}
$.ajax(ajaxOption).done(function (data) {
    console.log(data);
});

// php
<?php
require_once("../init.php");
$data = Post('data');
?>



// AFTER (res는 배열)
// js
let dataObject = new Object();
dataObject = Object.assign({}, res);
const ajaxOption = {
    url: API_URL + `/REQUEST/postList.php`,
    async: true,
    type: "POST",
    data: {
        "data": res,
    },
    dataType: "html",
    cache: false,
    };
}
$.ajax(ajaxOption).done(function (data) {
    console.log(data);
});

//php
<?php
require_once("../init.php");
$data = $_POST["data"];
?>