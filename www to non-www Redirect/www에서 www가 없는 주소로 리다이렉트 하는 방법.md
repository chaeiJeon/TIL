# 해결 과정에서 생긴 문제

/etc/apache2/sites-enabled 안에 000-default-le-ssl.conf, 000-default.conf 두 파일이 있었는데 어떤 파일이 웹 서버에서 실행되는 파일인지 모르겠어서 config 파일을 뒤졌다.

config 파일을 보니 virtual host configurations는 IncludeOptional sites/enabled/*.conf 로 명시되어 있었다.
=> 둘 다 포함한다는 의미

그래서 실제로 포함되고 있는 파일이 맞는지 000-default.conf 파일 안 내용을 모두 주석처리 하고 라이브 서버가 돌아가는지 확인해보니 문제없이 동작하고 있었다. (왜인지 모르겠어서 5시간을 헤메버림)

알고보니 000-default-le-ssl.conf는 443번 포트, 즉 https를 위한 config 파일이었고,
000-default.conf는 80번 포트, http를 위한 config 파일이었다.

우리 라이브 서버는 https로만 접속되게 되어있으니 000-default.conf를 아무리 바꾸어도 영향이 가지 않았던 것이다.

각 config 파일의 맨 위에 명시되어 있다.

<VirtualHost *:80>

~~

</VirtualHost>

이렇게.. ㅋㅋ





# 본 문제 해결 과정

그래서 해결하려 했던 문제인 리다이렉트 문제는

000-default-le-ssl.conf의 파일에

RewriteEngine On
RewriteCond %{SERVER_NAME} ^www.aibver.com [NC]
RewriteRule ^(.*)$ https://aibver.com/$1 [L,R=301]

이 내용을 추가해주어서 해결하였다.
