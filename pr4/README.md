Практическая работа 4 Network Threat Hunting

Колонин А.Н. ББМО-02-23

Скачиваем и разворачиваем стенд

![image](https://github.com/user-attachments/assets/ee2cb16b-3123-4e31-b899-09b215beada0)

![image](https://github.com/user-attachments/assets/459b5163-6bae-46a3-8ea7-c99e7039bc11)

В соответствии с руководством добавляем адрес с траффиком к skype.com в safelist

![image](https://github.com/user-attachments/assets/1f2da347-011a-4abb-8bab-d3fdc5cfe71b)

![image](https://github.com/user-attachments/assets/774ed24f-81c2-4c78-8555-3d81f27fc594)

Проверяем сам safelist

![image](https://github.com/user-attachments/assets/cb5982c1-8901-4bdf-a0b4-90ea5e71985a)

Переходим к lab1. Импортируем логи и переключаемся на них в стенде

![image](https://github.com/user-attachments/assets/bf4adf53-87e2-4e55-8ebb-f1788f45ab01)

![image](https://github.com/user-attachments/assets/7c9e904e-857b-4c63-9216-66317a28867d)

Переходим в модуль beacon web, где проанализируем различные адреса

![image](https://github.com/user-attachments/assets/4e7adee9-7d80-41a7-89ac-9abb54c6eb2a)

Первый же адрес выглядит подозрительно. Очень высокий beacon score, много соединений (3011), гистограмма довольно плоская, пользовательский агент идентифицируется как Windows 7, нет строки хоста, должно идентифицироваться полное доменное имя веб-сервера

Второй адрес

![image](https://github.com/user-attachments/assets/ca1cd822-4001-4fde-8f83-b41f31e74108)

Хост оптимизации MS delivery, легитимный

Третий адрес

![image](https://github.com/user-attachments/assets/617ef8ce-6da3-4d97-a52b-233177ca5b1b)

Windows tile services, можно добавить в safelist. Остальные адреса также связаны с Windows, поэтому начнём добавление в safelist

![image](https://github.com/user-attachments/assets/22658191-f6ee-4d19-8a80-938550a94655)

![image](https://github.com/user-attachments/assets/d751eaa6-11cc-45b8-820d-982a8c920fd9)

Остался только самый первый адрес

![image](https://github.com/user-attachments/assets/40a05184-248e-460f-830a-4771877b1dfe)

Теперь перейдём в модуль длительных соединений

![image](https://github.com/user-attachments/assets/c12a87a2-6c27-4c89-b591-df21209a159c)

Всего два адреса. Проверим первый на virus total

![image](https://github.com/user-attachments/assets/3913a620-9434-47bb-ae38-72dbb566f729)

Видим, что один из вендоров пометил его, как вредоносный

Второй адрес

![image](https://github.com/user-attachments/assets/fe970cae-b072-4626-8ad4-de11d13c996b)

Windows notification services, легитимный

Рассмотрим первый адрес на AbuseIPDB

![image](https://github.com/user-attachments/assets/87aefe45-7063-48d2-b443-3692fc824715)

Вывод

Соединения с 104.248.234.238 выглядят очень подозрительно:
нет запросов FQDN,
3011 соединений с высоким beacon score,
смена строки пользовательского агента,
нет поля «хост» в HTTP-заголовке,
длинная запутанная строка URI,
погуглив "rmvk30g" выдаётся "Fiesta EK".
Все остальные записи могут быть помещены в safelist.

Переходим к lab2. Импортируем логи и переключаемся на них.

![image](https://github.com/user-attachments/assets/92ab9b67-91a3-41a0-9553-297530d03479)

![image](https://github.com/user-attachments/assets/0374c09e-3558-47d8-95ce-d469e0a41eef)

На основной странице пусто, но система отсылается к модулю DNS

![image](https://github.com/user-attachments/assets/a3c4c305-b1ed-49e1-9360-862904f590e1)

![image](https://github.com/user-attachments/assets/22220e49-e2b7-4e22-a56a-c49c5129d0a0)

Видим множество обращений на поддомены honesimnotevil.com

Вывод

Потенциальный C2 через DNS. Похоже на dnscat2

Переходим к lab3, повторяем аналогичные действия

![image](https://github.com/user-attachments/assets/28fcffb1-1935-4d15-9680-3e1ed1a166fe)

![image](https://github.com/user-attachments/assets/f300c4c9-0fbd-4ece-b03c-97347b5fae4e)

Переходим в модуль beacons web, как в lab1

![image](https://github.com/user-attachments/assets/cd978a58-e038-4b2e-b658-cf78ed8d6f39)

Всего два адреса, проверим каждый через virus total

![image](https://github.com/user-attachments/assets/7bcd4319-27cf-433a-bd7f-862b85471b25)

Первый же адрес выглядит подозрительно: гистограмма плоская, пользовательский агент и FQDN выглядят фальшиво

Второй адрес

![image](https://github.com/user-attachments/assets/5960180a-e0de-4a9b-9b7e-2849e6b6f0fc)

Связан с microsoft, можно добавить в safelist

![image](https://github.com/user-attachments/assets/67e5b49d-8b90-431b-ab43-91030e227574)

Вкладка длительных соединений идентична lab1. Следовательно, первый адрес вредоносный
