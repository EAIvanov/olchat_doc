# Roistat

### Настройка виджета

1. Зайдите в настройки коннектора
2. В разделе «Настройка виджета на сайт» в текст приветственного сообщения  добавьте идентификатор Roistat **{roistat\_visit}**

<figure><img src="../.gitbook/assets/image (1034).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Обратите внимание, что если клиент удалит параметр **{roistat\_visit}** из первого отправляемого сообщения, данные аналитики вы получить не сможете!

Для того, чтобы клиент был заинтересован в отправке сообщения с параметром **{roistat\_visit}**, вы можете проявить креативность и как-то модифицировать текст сообщения. Например, таким образом: «Здравствуйте! Мой код для получения подарка: **{roistat\_visit}**»
{% endhint %}

### Настройка сайта

Модифицируйте на сайте код следующим образом:

```
<script>

window.roistatVisitCallback = function (visitId) {
    const b24w = setInterval(() => {
        const l = document.querySelector('[data-b24-crm-button-widget=openline_olchat_wa_connector_2]');
        if (l !== null) {
            clearInterval(b24w);
            l.href = l.href.replace(/\{roistat_visit\}/, visitId);
        }
    }, 250);
}

/* КОД ВИДЖЕТА БИТРИКС24 */

/* КОД АНАЛИТИКИ ROISTAT */



</script>
```
