# Переменные значения в роботах и активити бизнес-процессов

При работе с роботами и активити бизнес-процессов в полях есть возможность указывать как собственный текст (заданный вручную), так и использовать различные переменные значения (поля документа и прочие данные, которые могут меняться и поэтому не задаются вручную). Для подстановки таких переменных значений используется специальная форма «Вставка значения».

Чтобы вызвать форму вставки значения в роботах, напротив нужного поля нажмите на иконку три точки «▪▪▪»

<figure><img src="../.gitbook/assets/image (357).png" alt=""><figcaption></figcaption></figure>

В активити бизнес-процессов вызов формы также осуществляется с помощью нажатия на соответствующую кнопку напротив поля:

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

Значение, которое вставляется с помощью формы «Вставка значения» заключено в двойные фигурные скобки и имеет вид:

<figure><img src="../.gitbook/assets/image (493).png" alt=""><figcaption></figcaption></figure>

В этом случае, при срабатывании робота вместо значения **\{{Рабочий телефон\}}** произведётся подстановка номера телефона из карточки сущности.

В качестве переменного значения могут выступать следующие данные:

* Параметры шаблона
* Переменные
* Константы
* Поля документа
* Дополнительные результаты
* Пользователи
* Категории пользователей

{% hint style="info" %}
Более подробная информация о форме «Вставка значения» и описание переменных значений содержится в статье от Битрикс24 [Вставка значения](https://helpdesk.bitrix24.ru/open/5426411/)
{% endhint %}

{% hint style="info" %}
Примеры настройки роботов OLChat с использованием переменных значений содержатся во всех статьях из раздела Роботы и Действия бизнес-процессов а также в кейсе[avtomatizaciya-voronki-po-meropriyatiyam-s-pomoshyu-uvedomlenii-v-whatsapp.md](../keisy/klienty/avtomatizaciya-voronki-po-meropriyatiyam-s-pomoshyu-uvedomlenii-v-whatsapp.md "mention")&#x20;
{% endhint %}
