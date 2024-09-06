---
description: Передача параметра ClientID Яндекс.Метрики
---

# Яндекс.Метрика ClientID

### Настройка виджета

1. Зайдите в настройки коннектора
2. В разделе «Настройка виджета на сайт» добавьте параметр **{visit\_id}** в текст приветственного сообщения

<figure><img src="../.gitbook/assets/image (1033).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Обратите внимание, что если клиент удалит параметр **{visit\_id}** из первого отправляемого сообщения, данные аналитики вы получить не сможете!

Для того, чтобы клиент был заинтересован в отправке сообщения с параметром **{visit\_id}**, вы можете проявить креативность и как-то модифицировать текст сообщения. Например, таким образом: «Здравствуйте! Мой код для получения подарка: **{visit\_id}**»
{% endhint %}

### Настройка сайта

Добавьте на ваш сайт код передачи параметра в виджет.\
Где ХХХХХХХХ — номер вашего счётчика Яндекс.Метрики

{% hint style="info" %}
Рекомендуем размещать код сразу после кода счётчика Метрики.
{% endhint %}

```javascript
<script>
	const b24w = setInterval(() => {
		const l = document.querySelector('[data-b24-crm-button-widget=openline_olchat_wa_connector_2]')
		if (l !== null) {
			clearInterval(b24w)
			ym(XXXXXXXX, 'getClientID', (clientID) => l.href=l.href.replace(/\{visit_id\}/, clientID))
		}
	}, 250)
</script>
```

В некоторых случаях счётчик Яндекс.Метрики не успевает загрузиться и передать параметр clientID в **{visit\_id}**. В этом случае нужно дополнить код счётчика [параметром проверки инициализации счётчика](https://yandex.ru/support/metrica/code/counter-initialize.html#counter-initialize\_\_check-initialize). Для этого добавьте в код счётчика параметр triggerEvent

```javascript
ym(XXXXXX, "init", {triggerEvent: true});
```

В данном случае код подмены параметра  **{visit\_id}** будет выглядеть так:

```javascript
<script>
	document.addEventListener('yacounterXXXXXXXXinited', () => {
	    const b24w = setInterval(() => {
			const l = document.querySelector('[data-b24-crm-button-widget=openline_olchat_wa_connector_2]')
			if (l !== null) {
				clearInterval(b24w)
				ym(XXXXXXXX, 'getClientID', (clientID) => l.href=l.href.replace(/\{visit_id\}/, clientID))
			}
		}, 250)
	})
</script>
```

{% hint style="info" %}
Если вы используете Google Tag Manager, то скорее всего вы получите ошибку при публикации тега. Дело в том, что GTM немного староват и не поддерживает современный Java Script. Чтобы всё прошло гладко, модифицируйте код следующим образом, убрав константы и стрелочные функции:
{% endhint %}

```javascript
<script>
  document.addEventListener('yacounterXXXXXXXXinited', function () {
    var b24w = setInterval(function () {
      var l = document.querySelector('[data-b24-crm-button-widget=openline_olchat_wa_connector_2]');
      if (l !== null) {
        clearInterval(b24w);
        ym(XXXXXXXX, 'getClientID', function (clientID) {
          l.href = l.href.replace(/\{visit_id\}/, clientID)
        });
      }
    }, 250);
  });
 </script>
```
