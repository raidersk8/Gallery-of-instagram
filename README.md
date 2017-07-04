<h1>Gallery of instagram</h1>
#Регестрируем нового клиента https://www.instagram.com/developer/clients/manage/<br />
из важного Valid redirect URIs сайт на котором хотите выводить галерею<br />

<h1>Получаем токен</h1>
https://api.instagram.com/oauth/authorize/?client_id=CLIENT-ID&redirect_uri=REDIRECT-URI&response_type=token<br />
CLIENT-ID из Manage Client(https://www.instagram.com/developer/clients/manage/)<br />
REDIRECT-URI тот что указали при регистрации(Valid redirect URIs)<br />
Нас перебросить на наш сайт где в адресной строке будет токен<br />

<h1>пример получения фотографиий из инстаграм</h1>
$token = '';<br />
$user_id = 'self';<br />
$instagram_cnct = curl_init(); // инициализация cURL подключения<br />
curl_setopt( $instagram_cnct, CURLOPT_URL, "https://api.instagram.com/v1/users/" . $user_id . "/media/recent?access_token=" . $token ); // подключаемся<br />
curl_setopt( $instagram_cnct, CURLOPT_RETURNTRANSFER, 1 ); // просим вернуть результат<br />
curl_setopt( $instagram_cnct, CURLOPT_TIMEOUT, 15 );<br />
$media = json_decode( curl_exec( $instagram_cnct ) ); // получаем и декодируем данные из JSON<br />
curl_close( $instagram_cnct ); // закрываем соединение<br />
