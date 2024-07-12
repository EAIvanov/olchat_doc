# Calltouch

### Настройка виджета

1. Зайдите в настройки коннектора
2. В разделе «Настройка виджета на сайт» добавьте параметр **{visit\_id}** в текст приветственного сообщения

<figure><img src="../.gitbook/assets/image (1034).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Обратите внимание, что если клиент удалит параметр **{visit\_id}** из первого отправляемого сообщения, данные аналитики вы получить не сможете!

Для того, чтобы клиент был заинтересован в отправке сообщения с параметром **{visit\_id}**, вы можете проявить креативность и как-то модифицировать текст сообщения. Например, таким образом: «Здравствуйте! Мой код для получения подарка: **{visit\_id}**»
{% endhint %}

### Настройка сайта

Модифицируйте на сайте код следующим образом:

<pre><code>&#x3C;script>

	const b24w = setInterval(() => {
        const l = document.querySelector('[data-b24-crm-button-widget=openline_olchat_wa_connector_2]');
        if (l !== null) {
            const sessionId= window.ct('calltracking_params', '<a data-footnote-ref href="#user-content-fn-1">mod_id</a>').sessionId;
console.log(sessionId);
            if (sessionId) {
                clearInterval(b24w);
                console.log(sessionId);
                l.href = l.href.replace(/\{visit_id\}/, sessionId);
            }
        }
    }, 250);

/* КОД ВИДЖЕТА БИТРИКС24 */

/* КОД АНАЛИТИКИ CALLTOUCH */



&#x3C;/script>
</code></pre>

[^1]: mod\_id - уникальный идентификатор скрипта, который можно просто скопировать вместе со сгенерированным идентификатором из настроек вашего проекта в личном кабинете Calltouch
