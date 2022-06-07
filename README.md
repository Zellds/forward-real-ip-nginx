> ## FORWARD-REAL-IP
>
>
> ### Repositório com o intuito de solucionar um problema em que o IP REAL nao chega ao log do PHP-FPM.
> 
> O que ocorre é que ao passar por diferentes IP, como ao fazer um **PROXY**, apenas o cabeçalho **X-Forwarded-For** pode nao funcionar corretamente, 
> para isso, em minha configuração do **[custom-phpfpm.conf](https://github.com/Zellds/forward-real-ip-nginx/blob/8baad4fed69c80f76edea377aa9d42b3ff1f6cd1/docker/php-fpm/custom-phpfpm.conf)** 
> foi necessario no formato do log, adicionar um parametro para conseguir extrair a informação correta, 
> que neste caso foi **``%{HTTP_X_REAL_IP}e``** deixando a minha formatação completa do log da seguinte maneira **``access.format = "%t \"%m %r%Q%q\"%{HTTP_X_REAL_IP}e"``**, 
> agora conferindo o log, ja deve constar a informação correta.
>
> Confira os parametros usados e outros em = https://www.php.net/manual/pt_BR/install.fpm.configuration.php#126422
>
