# REST API для работы с WhatsApp

Мы добавили в OLChat REST API для работы с WhatsApp! Теперь вы можете сформировать вебхук и использовать его для вызовов методов REST в своих сценариях автоматизации и при интеграции различных сервисов.

### Получение вебхука

Создать вебхук можно зайдя в приложение **OLChat — Коннектор — Права доступа к коннектору — Вебхук — СОЗДАТЬ ВЕБХУК**

<figure><img src="../.gitbook/assets/image (760).png" alt=""><figcaption></figcaption></figure>

После создания, вебхук можно при необходимости изменить, нажав на кнопку «ИЗМЕНИТЬ ВЕБХУК».

<figure><img src="../.gitbook/assets/image (290).png" alt=""><figcaption></figcaption></figure>

### Описание методов

Для простоты использования, большая часть API допускает использование GET-запросов.&#x20;

{% swagger method="get" path="sendText" baseUrl="https://olchat.infocom.io/rest/webhook/wa/{{token}}/" summary="Отправка сообщения" %}
{% swagger-description %}
Позволяет отправить текстовое сообщение на указанный номер телефона в WhatsApp.

Ограничение: 5 запросов в 3 секунды
{% endswagger-description %}

{% swagger-parameter in="path" name="phone_number" required="true" type="str" %}
Номер телефона
{% endswagger-parameter %}

{% swagger-parameter in="path" name="body" required="true" type="text" %}
Тело сообщения
{% endswagger-parameter %}

{% swagger-parameter in="path" name="send_to_imol" type="Y|N" required="true" %}
Отправка в чат Открытой Линии. Может принимать значение Y|N
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="sendFile" baseUrl="https://olchat.infocom.io/rest/webhook/wa/{{token}}/" summary="Отправка файла" %}
{% swagger-description %}
Позволяет отправить файл на указанный номер телефона в WhatsApp. В качестве файла указывается прямая ссылка на файл. Подробнее в статье [#sozdanie-pryamoi-ssylki-na-fail](../roboty-i-aktiviti/sozdanie-pryamoi-ssylki-na-fail.md#sozdanie-pryamoi-ssylki-na-fail "mention").

Ограничение: 5 запросов в 3 секунды
{% endswagger-description %}

{% swagger-parameter in="path" name="phone_number" required="true" type="str" %}
Номер телефона
{% endswagger-parameter %}

{% swagger-parameter in="path" name="body" required="true" type="url" %}
Прямая ссылка на файл
{% endswagger-parameter %}

{% swagger-parameter in="path" name="send_to_imol" type="Y|N" required="true" %}
Отправка в чат Открытой Линии. Может принимать значение Y|N
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="checkPhone" baseUrl="https://olchat.infocom.io/rest/webhook/wa/{{token}}/" summary="Проверка WA на номере" %}
{% swagger-description %}
Позволяет проверить наличие на номере аккаунта WhatsApp.

Ограничение: 3 запроса в 1 секунду

**ВАЖНО! Не злоупотребляйте этим методом, т.к. высока вероятность блокировки вашего аккаунта со стороны WhatsApp**
{% endswagger-description %}

{% swagger-parameter in="path" name="phone_number" type="str" required="true" %}
Номер телефона
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="checkStatus" baseUrl="https://olchat.infocom.io/rest/webhook/wa/{{token}}/" summary="Проверка статуса линии" %}
{% swagger-description %}
Позволяет проверить статус текущей линии.

Ограничение: 5 запросов в 3 секунды
{% endswagger-description %}
{% endswagger %}

{% swagger method="get" path="checkMessageStatus" baseUrl="https://olchat.infocom.io/rest/webhook/wa/{{token}}/" summary="Проверка статуса сообщения" %}
{% swagger-description %}
Ограничение: 5 запросов в 3 секунды
{% endswagger-description %}

{% swagger-parameter in="path" name="phone_number" type="str" required="true" %}
Номер телефона
{% endswagger-parameter %}

{% swagger-parameter in="path" name="message_id" type="str" required="true" %}
ID сообщения
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}
{% endswagger %}

### Где можно использовать REST API

Предположим, что у вас есть сайт или интернет-магазин который не интегрирован с Битрикс24, но, присутствует необходимость уведомить клиента заполнившего форму на WhatsApp о том, что его заявка принята в работу или заказ оформлен.

Вы можете привязаться к событию заполнения формы и отправить запрос, содержащий метод отправки сообщения: **https://olchat.infocom.io/rest/webhook/wa/\{{token\}}/sendText**

* В качестве **phone\_number** передайте в запрос номер телефона из формы
* В качестве **body** – ваш текст сообщения, например: «Мы получили вашу заявку, номер вашего заказа №00001»
* В **send\_to\_imol** передайте Y или N
