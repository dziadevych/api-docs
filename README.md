<p align="center">
  <img src="https://raw.githubusercontent.com/kunadevelopers/api-docs/master/kuna_api.png" title="Kuna API v3 Documentation" alt="kuna api v3 doc" />
</p>


[kuna.io]: https://kuna.io
[api.kuna.io]: https://api.kuna.io


[Библиотеки для работы с API v3]: #библиотеки-для-работы-с-api-v3

[Схема и сериализация данных в API]: #схема-и-сериализация-данных-в-api
  [Запросы]:                                    #запросы
  [Домен]:                                      #домен
  [Заголовки (Headers)]:                        #заголовки-headers
  [Подпись для приватных методов]:              #подпись-для-приватных-методов
  [Пример подписи с использованием JavaScript]: #пример-подписи-с-использованием-javascript
  [Пример приватного метода с cURL]:            #пример-приватного-метода-с-curl

[Публичные методы]: #публичные-методы
  [Время на сервере]: #время-на-сервере
  [Список доступных валют]: #список-доступных-валют
  [Курс валют на бирже]: #курс-валют-на-бирже
  [Рынки]: #рынки
  [Последние данные по рынку (тикеры)]: #последние-данные-по-рынку-тикеры
  [Ордербук]: #ордербук
  [История сделок]: #история-сделок
  [График изменения цены]: #график-изменения-цены
  [Комиссии на ввод и вывод]: #комиссии-на-ввод-и-вывод

[Приватное и торговое API]: #приватное-и-торговое-api
  [Данные аккаунта]: #данные-аккаунта
  [Баланс аккаунта]: #баланс-аккаунта
  [Создать ордер]: #создать-ордер
  [Список активных ордеров]: #список-активных-ордеров
  [Список исполненных ордеров]: #список-исполненных-ордеров
  [Список сделок по ордеру]: #список-сделок-по-ордеру
  [Отменить ордер]: #отменить-ордер

[Ввод и вывод криптовалюты]: #ввод-и-вывод-криптовалюты
  [Получить адрес для депозита]: #получить-адрес-для-депозита
  [Сгенерировать новый адрес для депозита]: #сгенерировать-новый-адрес-для-депозита
  [Создание заявки на вывод криптовалюты]: #cоздание-заявки-на-вывод-криптовалюты
  [Получить статус заявки на вывод]: #получить-статус-заявки-на-вывод
  [Получить историю вводов и выводов]: #получить-историю-вводов-и-выводов

[Ввод и вывод фиата]: #ввод-и-вывод-фиата
  [Получение публичного ключа для каждой из валют]: #получение-публичного-ключа-для-каждой-из-валют

[Kuna Codes]: #kuna-codes
  [Валидация кода offline (по чексумме)]:   #валидация-кода-offline-по-чексумме
  [Статусы кодов]:                          #статусы-кодов
  [API объект Kuna Code]:                   #api-объект-kuna-code
  [Проверить Kuna Code]:                    #проверить-kuna-code
  [Создать Kuna Code]:                      #создать-kuna-code
  [Активировать Kuna Code]:                 #активировать-kuna-code
  [Получить информацию о Kuna Code по ID]:  #получить-информацию-о-kuna-code-по-id
  [Список выпущенных кодов]:                #список-выпущенных-кодов
  [Список активированных кодов]:            #список-активированных-кодов


# Документация по Kuna API v3

API планировалось быть организованым по принципам REST. Но что-то пошло не так. \
Все методы делятся на публичные (public) и приватные (private).

Для того что бы осуществлять приватные запросы, вы должны быть зерегистрированным пользователем на сайте [kuna.io], и иметь специальный **API Token**, который состоит из публичного (`publicKey`) и приватного (`secretKey`) ключей. Используя приватный ключ, нужно сформировать запрос на каждую подпись. Подробнее расписано в разделе [Подпись для приватных методов].

Для публичных методов, публичный ключ и подпись запроса не нужны.

API Token можно получить у себя в кабинете, по ссылке https://kuna.io/api_tokens.


Оглавление
----------

* [Библиотеки для работы с API v3]
* [Схема и сериализация данных в API]
  * [Запросы]
  * [Домен]
  * [Заголовки (Headers)]
  * [Подпись для приватных методов]
  * [Пример подписи с использованием JavaScript]
  * [Пример приватного метода с cURL]

* [Публичные методы]
  * [Время на сервере]
  * [Список доступных валют]
  * [Курс валют на бирже]
  * [Рынки]
  * [Последние данные по рынку (тикеры)]
  * [Ордербук]
  * [История сделок]
  * [Комиссии на ввод и вывод]

* [Приватное и торговое API]
  * [Данные аккаунта]
  * [Баланс аккаунта]
  * [Создать ордер]
  * [Список активных ордеров]
  * [Список исполненных ордеров]
  * [Список сделок по ордеру]
  * [Отменить ордер]

* [Ввод и вывод криптовалюты]
  * [Получить адрес для депозита]
  * [Сгенерировать новый адрес для депозита]
  * [Создание заявки на вывод криптовалюты]
  * [Получить статус заявки на вывод]
  * [Получить историю вводов и выводов]

* [Ввод и вывод фиата]
  * [Получение публичного ключа для каждой из валют]

* [Kuna Codes]
  * [Валидация кода offline (по чексумме)]
  * [Статусы кодов]
  * [API объект Kuna Code]
  * [Проверить Kuna Code]
  * [Создать Kuna Code]
  * [Активировать Kuna Code]
  * [Получить информацию о Kuna Code по ID]
  * [Список выпущенных кодов]
  * [Список активированных кодов]


Библиотеки для работы с API v3
------------------------------
Наши проекты находятся в стадии разработки. Мы их выпустим сразу как только будем уверены что они безопасны и стабильны.

**Проекты от комьюнити** \
На свой страх и риск, вы можете использовать реализации API v3 от комъюнити.

JavaScript библиотека: [CoinWizard/kuna-sdk](https://github.com/CoinWizard/kuna-sdk) \
[![NPM Version](https://img.shields.io/npm/v/kuna-sdk.svg?style=flat)](https://www.npmjs.com/package/kuna-sdk)
[![NPM Downloads](https://img.shields.io/npm/dm/kuna-sdk.svg?style=flat)](https://www.npmjs.com/package/kuna-sdk)




Схема и сериализация данных в API
---------------------------------
### Запросы
Доступ к данным осуществляется через стандартные HTTPS запросы в кодировке UTF-8. Данные отправляется и принимаются в формате JSON.


### Домен
Для всех методов, публичных или приватных, используеся один домен
```bash
https://api.kuna.io
```


К примеру, URL для получения актуального ордербука
```bash
https://api.kuna.io/v3/book/{market}
```
где `{market}` это ключ пары, `btcuah`, `kunbtc` или другой


### Заголовки (Headers)
Заголовки, которые нужны для успешного запроса.

| Заголовок       | Описание                       |
|-----------------|--------------------------------|
| `Accept`        | Должен быть `application/json` |
| `Content-Type`  | Только для методов где есть тело. Должен быть `application/json` |
| `Kun-Nonce`     | Метка времени запроса. Указывается в формате Unix Time Stamp в милисекундах (ms). Только для приватных методов. |
| `Kun-ApiKey`    | Публичный ключ вашего API Token. Только для приватных методов. |
| `Kun-Signature` | Подпись запроса. Только для приватных методов. |



### Подпись для приватных методов
Подпись нужно указать в заголовке запроса под ключем `Kun-Signature`.

Она формируется по формуле
```
HEX(
    HMAC-SHA384(
      {apiPath} + {nonce} + JSON({body}),
      {secretKey}
    )
)
```

Где,

| Значение        | Описание                                     |
| --------------- | -------------------------------------------- |
| `{apiPath}`     | Метод, к примеру `/v3/auth/kuna_codes/count` |
| `{nonce}`       | Метка времени запроса. Указывается в формате Unix Time Stamp в милисекундах (ms). Это же значние должно быть и в заголовке под ключем `Kun-Nonce` |
| `{body}`        | Данные, которые передаются в теле запроса. Должны быть в формате JSON. В случае `GET` методов, когда тело не передается, используется пустой JSON объект - `{}`. |
| `{secretKey}`   | Приватный ключ вашего API Token              |


#### Пример подписи с использованием JavaScript

```javascript
const crypto = require('crypto');

const publicKey = '';
const secretKey = '';

const apiPath = '/v3/auth/kuna_codes/issued-by-me';
const nonce = new Date().getTime();
const body = {};

const signatureString = `${apiPath}${nonce}${JSON.stringify(body)}`;

const signature = crypto
    .createHmac('sha384', secretKey)
    .update(signatureString)
    .digest('hex');

console.log(signature); // выводит подпись в HEX формате
```


### Пример приватного метода с cURL

```bash
curl -X POST \
    https://api.kuna.io/v3/auth/kuna_codes/issued-by-me \
    -H 'Accept: application/json' \
    -H 'Kun-Nonce: 1560007410000' \
    -H 'Kun-ApiKey: vPNvF9ArqV4HqMzpAIyaLvToJJ1x1rfRZP5jNrQf' \
    -H 'Kun-Signature: 0d34c19a5125d68fe2e7fb3a3b58e162cc53e166d1e7790deb5d79f6cb04aad1d5e01daeb3ecf8871c3b767a8ea289ea'
```
###### Не пытайтесь использовать этот API Key. Он для примера :)



Публичные методы
----------------
### Время на сервере
Этот метод возвращает текущее время на сервере Kuna. Полезно, если нужно проверить доступность API.

```
GET /v3/timestamp
```

**Пример ответа**
```bash
{
  "timestamp": 1560005994,
  "timestamp_miliseconds": 1560005994692
}
```


### Список доступных валют
Вернет список валют, доступных на Kuna.

```
GET /v3/currencies
```

**Пример ответа**
```bash
[
  {
    "id": 2,            # внутренний ID
    "code": "btc",      # символ валюты
    "name": "Bitcoin",  # имя валюты
    "has_memo": false,  # нужно ли для этой валюты Memo
    "icons": {
      "std": "https://kuna.io/icons/currency/std/btc.svg",
      "xl": "https://kuna.io/icons/currency/xl/btc.svg",
      "png_2x": "https://kuna.io/icons/currency/png/BTC@2x.png",
      "png_3x": "https://kuna.io/icons/currency/png/BTC@3x.png"
    },
    "coin": true,       # является ли валюта криптовалютой
    "explorer_link":    # шаблон ссылки для TXID в експлорере
      "https://www.blockchain.com/btc/tx/#{txid}",
    "sort_order": 5,    # позиция в сортировке
    "precision": {      # параметры округления чисел
      "real": 8,
      "trade": 6
    }
  }
]
```

### Курс валют на бирже
Этот метод позволяет вам получить курсы валют в USD, UAH, BTC, EUR и в рублике, для каждой из существующих валют на Kuna.

```
GET /v3/exchange-rates/{currency}
```

**Примеры запроса**
```bash
# вернет объект с курсами для USD
curl https://api.kuna.io/v3/exchange-rates/usd

# если не указать currency, то метод вернет массив всех доступных валют с их курсами
curl https://api.kuna.io/v3/exchange-rates
```

**Пример ответа для USD**
```bash
{
  "currency": "usd",  # ключ валюты
  "usd": 1,           # курс к доллару соединенных штатов
  "uah": 26.595721,   # курс к гривне Украины
  "btc": 0.0001276,   # курс к Bitcoin
  "eur": 1.13,        # курс к Евро
  "rub": 0.0153752    # курс к рублику
}
```


### Рынки
Этот метод возвращает список валютных пар (рынков), которые доступны для торговли.

```
GET /v3/markets
```

**Пример ответа**
```bash
[
  {
    "id": "btcusdt",        # ключ валютной пары
    "base_unit": "btc",     # базовая валюта
    "quote_unit": "usdt",   # валюта котировки
    "base_precision": 6,    # округление базовой валюты
    "quote_precision": 2,   # округление валюты котировки
    "display_precision": 1, # точность для групировки ордеров в ордербуке
    "price_change": -1.89   # изменение цены в % за 24 часа
  }
]
```


### Последние данные по рынку (тикеры)
Этот метод возвращает тикеры по всем рынкам, либо по конкретному.

Тикер представляет собой общий обзор состояния рынка. Он показывает текущую лучшую цену спроса и предложения, а также цену последней сделки. Он также включает в себя информацию, такую как дневной объем и сколько цена изменилась за последний день.

```
GET /v3/tickers?symbols={symbols}
```

**Примеры запроса**
```bash
# Вернет информацию по btcuah, kunbtc и ethuah
curl https://api.kuna.io/v3/tickers?symbols=btcuah,kunbtc,ethuah

# Вернет информацию только по рынку btcuah
curl https://api.kuna.io/v3/tickers?symbols=btcuah

# Вернет информацию по всем активным рынкам
curl https://api.kuna.io/v3/tickers?symbols=ALL
```

**Пример ответа**
```bash
[
  [
    "btcuah",   # символ рынка
    208001,     # цена BID
    11200693,   # объем ордербука BID
    208499,     # цена ASK
    29.255569,  # объем ордербука ASK
    5999,       # изменение цены за 24 часа в котируемой валюте 
    -2.8,       # изменение цены за 24 часа в процентах
    208001,     # последняя цена
    11.3878,    # объем торгов за 24 часа в базовой валюте
    215301,     # максимальная цена за 24 часа
    208001      # минимальная цена за 24 часа
  ]
]
```

### Ордербук
Этот метод позволяет вам получить актуальное состояние ордербука.

```
GET /v3/book/{symbol}
```

**Пример ответа**
```bash
[
  [
    208008,    # цена
    0.048076,  # обьем
    1          # количество заявок
  ],
  [
    212220,    # цена
    -0.091058, # обьем
    1          # количество заявок
  ]
]
```

Обратите внимание, весь ордербук для BID и ASK возвращается одним массивом.

Если обьем > 0, то имеем данные по ордерам BID . \
Если обьем < 0, то данные по ордерам ASK.


### История сделок

😱 _Coming soon_ \
Этот метод еще в разработке и появится в документации так скоро как сможем его показать.


### График изменения цены

😱 _Coming soon_ \
Этот метод еще в разработке и не готов к масовому использованию. Мы его опубликуем в документации так скоро, как сможем.


### Комиссии на ввод и вывод
Метод для получение списка активных способов ввода и вывода средств, а так-же комиссий на ввод или вывод криптовалюты.

```bash
GET /v3/fees
```

**Пример ответа**
```bash
[
  # пример для фиатной валюты
  {
    # способ вывода для фиатных валют
    # возможные варианты: advcash_wallet, payeer, perfectmoney_account,
    #                     perfectmoney_transfer, kuna_code, payment_card
    "code": "advcash_wallet",

    "category": "usd",    # символ фиатной валюты
    "deposit_fees": [     # процент или абсолютное значение для депозита
      {"type": "percent", "amount": "0.0"}
    ],
    "withdraw_fees": [    # процент или абсолютное значение для вывода
      {"type": "percent", "amount": "1.9"}
    ]
  }, 

  # пример для криптовалюты
  {
    "code": "kun",              # символ криптовалюты
    "category": "coin",         # в категории для криптовалюты всегда coin 
    "deposit_fees": [],         # криптовалюта на ввод не трубует дополнительных комиссий
    "withdraw_fees": [          # описание комиссий на вывод
      {
        "type": "fixed",        # комиссия всегда фиксированная
        "asset": {
          "amount": 0.01,       # размер комиссии
          "currency": "waves",  # криптовалюта в которой изымется комиссия
          "to_usd": "0.02"      # курс обмена 
        }
      }
    ],
    "min_deposit": {            # данные о минимальной сумме на депозита
      "amount": 1,
      "currency": "kun",
      "to_usd": "5.66"
    },

    "min_withdraw": {           # данные о минимальной сумме на вывода
      "amount": 1,
      "currency": "kun",
      "to_usd": "5.66"
    }
  }
]
```


Приватное и торговое API
------------------------
Каждый приватный метод требует подписи, механизм которой описан в \
**Схема и сериализация данных в API > Подпись для приватных методов**.


### Данные аккаунта
Данный метод возвращает данные об аккаунте, такие как Email, Kuna-ID, активна ли двухфакторная аутентификация.

```bash
POST /v3/auth/me
```

**Пример ответа**
```bash
{
  "email": "my-email@gmail.com",    # email аккаунта
  "kunaid": "kunaid-XXXXXXXXXXXX",  # Kuna ID аккаунте. Его можно сменить через сапорт.
  "two_factor": true,               # активирована ли двухфакторная аутентификация
  "withdraw_confirmation": false,   # нужно ли подтвердение через Email для вывода средств
  "public_keys": {                  # набор ключей для ввода-вывода фиата
    "deposit_sdk_uah_public_key": "pk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    "deposit_sdk_usd_public_key": "pk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    "deposit_sdk_rub_public_key": "pk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
  },
  "announcements": false
}
```


### Баланс аккаунта
Метод баланса аккаунта возвращает массив всех балансов всех валют вашего акаунта на Kuna вместе с информацией о достпных средствах.

```bash
POST /v3/auth/r/wallets
```

**Пример ответа**
```bash
[
  [
    'exchange', 
    'USD',      # символ валюты
    1208370,    # полный баланс аккаунта
    null,       # не используется
    1208370     # доступные средства
  ],
  [
    'exchange',
    'KUN',
    800000,
    null,
    760000
  ],
]
```


### Создать ордер

😱 _Coming soon_ \
Покачто, этот метод не доступен. Но вы можете создать новый ордер, [используя API v2](https://kuna.io/documents/api).


### Список активных ордеров
Этот метод вернет список всех ваших активных ордеров

```bash
POST /v3/auth/r/orders/{?markets}
```

**Примеры запроса**
```bash
# Вернет список всех активных ордеров
curl -X POST \
  "https://api.kuna.io/v3/auth/r/orders" \
  -d "{}"

# Вернет список активных ордеров только на паре BTC/UAH
curl -X POST \
  "https://api.kuna.io/v3/auth/r/orders/btcuah" \
  -d "{}"
```

**Пример ответа**
```bash
[
  [
    100279610,      # ID ордера
    null,           # не используется
    null,           # не используется
    'xrpuah',       # код рынка (валютной пары)
    1560089091000,  # время создания (timestamp в милисекундах)
    1560089091000,  # время обновления (timestamp в милисекундах)
    '45.0',         # объем ордера
    '-45.0',        # изначальный обьем ордера
                    # если значение < 0 то ордер на продажу
                    # если > 0, то ордер на покупку
    'LIMIT',        # тип ордера (LIMIT or MARKET)
    null,           # не используется
    null,           # не используется
    null,           # не используется
    null,           # не используется
    'ACTIVE',       # статус ордера
    null,           # не используется
    null,           # не используется
    '14.0',         # цена ордера
    '0.0'           # средняя сделок по ордеру
  ]
]
```


### Список закрытых ордеров
Этот метод вернет список закрытых ордеров

```bash
POST /v3/auth/r/orders/{?markets}/hist
```

**Примеры запросов**
```bash
# Вернет список закрытых ордеров ордеров для любой пары
curl -X POST \
  "https://api.kuna.io/v3/auth/r/orders/hist" \
  -d "{}"

# Вернет список закрытых ордеров только для пары BTC/UAH
curl -X POST \
  "https://api.kuna.io/v3/auth/r/orders/btcuah/hist" \
  -d "{}"
```

**Параметры тела запроса**

| Параметр   | Обязательный | Описание           |
|------------|--------------|--------------------|
| `start`    | нет          | Показать ордера с этой даты. Время в миллисекундах. По умолчанию 2 недели назад. |
| `end`      | нет          | Показать ордера до этой даты. Время в миллисекундах. По умолчанию текущее время.  |
| `limit`    | нет          | Количество записей. По умолчанию 25 |
| `sort`     | нет          | 1 или -1. Порядок сортировки ордеров. По умолчанию ордера возвращаются в порядке убывания. |


**Пример ответа**
```bash
[
  [
    100279610,      # ID ордера
    null,           # не используется
    null,           # не используется
    'xrpuah',       # код рынка (валютной пары)
    1560089091000,  # время создания (timestamp в милисекундах)
    1560089091000,  # время обновления (timestamp в милисекундах)
    '45.0',         # объем ордера
    '-45.0',        # изначальный обьем ордера
                    # если значение < 0 то ордер на продажу
                    # если > 0, то ордер на покупку
    'LIMIT',        # тип ордера (LIMIT or MARKET)
    null,           # не используется
    null,           # не используется
    null,           # не используется
    null,           # не используется
    'EXECUTED',     # статус ордера
    null,           # не используется
    null,           # не используется
    '14.0',         # цена ордера
    '13.0'          # средняя сделок по ордеру
  ]
]
```


### Список сделок по ордеру

```bash
POST /v3/auth/r/order/{market}:{order_id}/trades
```


**Пример запроса**
```bash
# Вернет список сделок для ордера ID 10000000 в паре BTC/UAH
curl -X POST \
  "https://api.kuna.io/v3/auth/r/order/btcuah:10000000/trades" \
  -d "{}"
```


**Параметры запроса**

| Параметр           | Описание                                  |
|--------------------|-------------------------------------------|
| `market`           | Обязательный параметр. Код валютной пары. |
| `order_id`         | Обязательный параметр. ID ордера.         |


**Пример ответа**
```bash
[
  [
    2538815,            # ID сделки
    'ethuah',           # валютная пара
    1559667470000,      # время сделки
    98140806,           # ID ордера
    '0.032925',         # сумма сделки
    '6798.0',           # курс сделки
    null,               # не используется
    null,               # не используется
    -1,                 # 1 - maker, -1 taker
    '0.0000823125',     # размер комиссии
    'eth'               # валюта комиссии
  ]
]
```


### Отменить ордер
Этот метод позволяет отменить один или несколько активных ордеров.

```bash
POST /v3/order/cancel
```

**Пример запроса**
```bash
# Отменит ордер с ID 1000000 
curl -X POST \ 
  "https://api.kuna.io/v3/order/cancel"
  -d '{"order_id": 1000000}'

# А так можно отменить сразу несколько ордеров, ID 1000000 и ID 1000001
curl -X 'POST' \
  "https://api.kuna.io/v3/order/cancel/multy" \
  -d '{"order_ids": [1000000, 1000001]}'
```


**Пример ответа**
```bash
{
  "id": 100279610,                  # ID ордера
  "side": "sell",                   # Операция ордера - продажа или покупка
  "type": "limit",                  # Тип ордера, limit или market
  "price": "14.0",                  # Цена ордера
  "avg_execution_price": "0.0",     # Средняя цена сделок по ордеру
  "symbol": "xrpuah",               # Валютная пара ордера
  "timestamp": 1560089091000,       # Время закрытия ордера
  "original_amount": "45.0",        # Изначальный объем ордера
  "remaining_amount": "45.0",       # Объем ордера на момент закрытия
  "executed_amount": "0.0",         # Исполненный объем ордера 
  "is_cancelled": null,
  "is_hidden": null,
  "is_live": null,
  "was_forced": null,
  "exchange": null
}
```


Ввод и вывод криптовалюты
-------------------------
Все методы предназначеные для ввода и вывода криптовалюты являются приватными, а значит для каждого вам понадобится подпись. \
Если у вас включена двухфакторная аутентификация, то так-же, вам понадобится указывать **otp** пароль для некоторых запросов. 

![Kuna Deposit statuses](https://raw.githubusercontent.com/kunadevelopers/api-docs/master/deposit-status.png)

![Kuna Withdraw statuses](https://raw.githubusercontent.com/kunadevelopers/api-docs/master/withdraw-status.png)


### Получить адрес для депозита
С помощью этого метода можно узнать на какой адрес нужно зачислять средства. Если аккаунт на Kuna был только что создан, то скорее всего на аккаунте не будет сгенерированных адресов для депозита. В этом случае вам нужно сгенерировать адрес специально для криптовалюты.

```bash
POST /v3/auth/deposit/info
```

**Параметры запроса**

| Параметр             | Обязательный | Описание                            |
|----------------------|--------------|-------------------------------------|
| `currency` (string)  | да           | Код криптовалюты (btc, ltc, dash, eth и другие) |


**Пример ответа**

```bash
{ 
  # количество подтверждений для зачисления средств на баланс
  "confirmations": 1,

  # минимальный размер депозита
  "min_deposit": 1,

  # адрес для депозита
  "address": "rMtb2JEX8xmcgSKxCB7aZPDyzyVhbM2RzV",

  # мемо для криптовалют, которым нужен memo (xrp, eos, stellar)
  "memo": "259002573"
}
```

⚠️ Eсли адрес для депозита не был сгенерирован, то в поле `address` будет `null`. В этом случае вам нужно сгенерировать адрес для депозита с помощью следующего метода.


### Сгенерировать новый адрес для депозита
Этот метод позволяет создать новый адрес для депозита криптовалюты.

```bash
POST /v3/auth/payment_addresses
```

**Параметры запроса**

| Параметр             | Обязательный | Описание                            |
|----------------------|--------------|-------------------------------------|
| `currency` (string)  | да           | Код криптовалюты (btc, ltc, dash, eth и другие) |


**Пример ответа**

```bash
{
  "success": true
}
```

⚠️ Если адрес уже был создан, то при повторном вызове этого метода пройзойдет ошибка: \
`HTTP/1.1 400 Bad Request`



### Создание заявки на вывод криптовалюты
Этим методом можно запросить вывод криптовалюты

```bash
POST /v3/auth/withdraw
```

⚠️ Если у вас активировано подтверждение на вывод по почте, то при каждом выводе необходимо подтвердить заяку, перейдя по ссылке, которая прийдет на почту.

**Параметры запроса**

| Параметр                   | Обязательный | Описание                            |
|----------------------------|--------------|-------------------------------------|
| `withdraw_type` (string)   | да           | Код криптовалюты (btc, ltc, dash, eth и другие) |
| `amount` (float)           | да           | Сумма вывода (по умолчанию без учета комисcии) |
| `address` (string)         | да           | Адрес для вывода криптовалюты |
| `payment_id` (string)      | нет          | Memo / Tag / Payment ID. Дополнительны параметр который может быть нужен в таких криптовалютах как XRP, EOS, Stellar и др. |
| `allow_blank_memo` (bool)  | нет          | Вывод с пустым memo (payment_id) допускается только при значении `true` для этого параметра. |
| `withdrawall` (bool)       | нет          | Этот флаг говорит, что `amount` так-же должен включать комиссию. Полезно, если нужно вывести все средства с аккаунта. |


**Пример ответа**

```bash
[
  { 
    # статус заявки на вывод
    "status": "awaiting_confirmation",

    # сообщение новосозданной заявки
    "message": "Your withdrawal request has been successfully submitted.",

    # внутренний ID с которым можно запросить статус этой заявки
    "withdrawal_id": 586829
  }
]
```



### Получить статус заявки на вывод

```bash
POST /v3/auth/withdraw/details
```

**Параметры запроса**

| Параметр            | Обязательный | Описание                            |
|---------------------|--------------|-------------------------------------|
| `id` (int32)        | да           | ID заявки на вывод                  |

**Пример ответа**

```bash
{
  "id": 586829,                 # внутренний ID заявки

  # дата создания заявки на вывод
  "created_at": "2019-08-20T13:00:00+02:00",

  "destination": "<address>",   # адрес получателя
  "currency": "btc",            # криптовалюта
  "amount": "0.32",             # сумма которая зачислится на адрес
  "status": "string",           # статус заявки
  "txid": "",                   # TXID заявки 
  "sn": "Jey38kL3",             # уникальный номер для обращения в сапорт для уточнения статуса
  "fee": "0.0005",              # комиссия за вывод
  "total_amount": "0.3205",     # суммарно списано с баланса
  "reference_id": ""            # что это???
}
```


### Получить историю вводов и выводов
Этот метод позволяет получить информацию всех операциях вводах и выводах средств. 

```bash
POST /v3/auth/assets-history/{?type}
```

**Параметры пути метода `assets-history`**

| Параметр                | Описание                                       |
|-------------------------|------------------------------------------------|
| `type` (string)         | Не обязательный параметр для фильтрации операций по вводу или выводу. Если не указать, то метод вернет и вводы и выводы. `withdraws` - вернет только операции вывода с аккаунта. `deposits` - вернет только операции зачисления |



**Примеры запросов**

```bash
# Получить абсолютно все транзакции deposit/withdraw или переводы между аккаунтами
curl https://api.kuna.io/v3/auth/assets-history

# Получить только выводы и исходящие транзакции 
curl https://api.kuna.io/v3/auth/assets-history/withdraws

# Получить только зачисления на аккаунт
curl https://api.kuna.io/v3/auth/assets-history/deposits
```


**Параметры запроса**

| Параметр                 | Обязательный | Описание                                                                |
|--------------------------|--------------|-------------------------------------------------------------------------|
| `currency_ids` (int32[]) | нет          | Фильтровать операции по список ID валют. ID мо можно получить из метода `/v3/currencies` |
| `statuses` (string[])    | нет          | Фильтровать операции по нескольким из статусов `done`, `pending` или `canceled` |
| `date_from` (int32)      | нет          | Фильтровать операции от определенного времени. Время в секундах (Unit Time Stamp). |
| `date_to` (int32)        | нет          | Фильтровать операции до определенного времени. Время в секундах (Unit Time Stamp).  |
| `page` (int32)           | нет          | Номер страницы (по умолчанию 1)                                         |
| `per_page` (int32)       | нет          | Количество кодов на страницу (по умолчанию 20)                          |
| `order_by` (string)      | нет          | Сортировать по `created_at`, `amount` (по умолчанию `created_at`)       |
| `order_dir` (string)     | нет          | Порядок сортировки `asc` или `desc` (по умолчанию `desc`)               |


**Пример ответа**

```bash
{
  # всего вводов и выводов
  total_items: 1,

  # список операций
  items: [
    {
      # ID операции
      id: 581303,

      # тип `deposit` или `withdraw`
      type: 'deposit',

      # дата операции
      created_at: '2018-09-28T13:06:45Z',

      # адрес на который поступили средства
      destination: '3P32q2q9WNiMQdfxN2aVYKDaZofQaDcv65E',

      # ID криптовалюты, который можно получить в методе `/v3/currencies`
      currency: 7,

      # сумма операции
      amount: 1,

      # статус `done`, `pending` или `canceled`
      status: 'done'
    }
  ],

  # список валют всех операций в списке
  currencies: [
    'waves'
  ]
}
```



Ввод и вывод фиата
------------------
Ввод и вывод фиата на Kuna осущевствляется через сервис `pay.kuna.io`. В Kuna существует 3 фиатные валюты: UAH, USD и RUB. В этом разделе описана процедура для автоматизации процесса ввода и вывода средств. Все методы в Kuna приватные, а значит потребуют подписи.

### Получение публичного ключа для каждой из валют
Для некоторых методов для `pay.kuna.io` вам нужно получить публичный ключ для каждой из поддерживаемых валют. Для этого нужно использовать приватный метод `POST https://api.kuna.io/v3/auth/me` с которым вы получет JSON ответ, где будут 3 ключа:

```bash
{
  "public_keys": {
    # публичный ключ для UAH
    "deposit_sdk_uah_public_key": "pk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",

    # публичный ключ для USD
    "deposit_sdk_usd_public_key": "pk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",

    # публичный ключ для RUB
    "deposit_sdk_rub_public_key": "pk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"   
  }
}
```

Для ввода или вывода USD вам нужно использовать `deposit_sdk_usd_public_key`.

⚠️ _Данный функционал ввода и вывода фиата находится в разработке._


Kuna Codes
----------
Kuna имеет особый функционал для трансфера средств между аккаунтами, без комиссий и СМС. Он называется **Kuna Code**.

Kuna Code имеет структуру: \
**857ny**-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-KUN-KCode

Всего, тело Kuna Code состоит из 45 символов (или 9 сегментов по 5 символов) и суфикса.
1. Первый сегмент из 5-ти символов - это **публичная часть кода**.
2. Потом идет 8 сегментов по 5 символов, это **приватная часть** кода.
3. Суфикса `KUN-KCode`, это валюта и метка что это код от куны.


### Валидация кода offline (по чексумме)

Первые 45 символов сегенирированны случайно. Первый символ, это чексумма остальных 44. Используя первый символ можно валидировать Kuna Code не обращаясь на сервер [kuna.io]. Первый символ расчитывается как сумма остальных по модулю 58.

Алгоритм валидации KunaCode на JavaScript:

```javascript
function validateKunaCode(kunaCode) {
  const base58Alphabet = '123456789abcdefghijkmnopqrstuvwxyzABCDEFGHJKLMNPQRSTUVWXYZ';

  // Разбиваем KunaCode по строкам и берем тело, без суфикса
  const body = kunaCode.split('-').slice(0, -2).join('');

  // Берем первый символ кода
  const checksum = base58Alphabet.indexOf(body[0]);

  // Отделяем остальные 44 символа кода 
  const str = body.slice(1);
  let i = str.length;
  let sum = 0;

  // Пробегаемся по каждому символу и суммируем его позицию в алфавите base58
  while (i--) {
    sum += base58Alphabet.indexOf(str.charAt(i));
  }
  
  // Сверяем чексумму
  if (sum % 58 !== checksum) {
    // Выбрасываем ошибку, так как чексумма не верная
    throw new Error('Invalid checksum');
  }

  return true;
}
```



### Статусы кодов

| Название статуса   | Описание                      |
|--------------------|-------------------------------|
| `created`          | Был создан                    |
| `processing`       | В процессе выпуска            |
| `unconfirmed`      | Ожидает подтверждения         |
| `active`           | Можно активировать            |
| `redeeming`        | В процессе активации          |
| `redeemed`         | Активирован                   |
| `onhold`           | Под подозрением               |
| `canceled`         | Отменен                       |


### API объект Kuna Code
Почти все методы возвращают одинаковую структуру данных для Kuna Code. Будь то создание, или получение конкретного кода, или получение списка кодов, вы всегда получите такие данные:

```bash
{
  # внутренний ID
  "id": 519,

  # ID для указания к супорту
  "sn": "p9MajCjlLo72",

  # секретный ключ кода, по которому он и активируется
  "code": "857ny-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-KUN-KCode",

  # Kuna-ID того кто может активировать код.
  # если 'all' то активировать может кто угодно
  "recipient": "all",

  # сумма кода
  "amount": "800000",

  # валюта кода
  "currency": "kun",

  # статус кода
  "status": "active",

  # время, до которого нельзя активировать код владельцем
  "non_refundable_before": "2019-08-20T13:00:00+02:00",

  # время создания кода
  "created_at": "2019-03-20T13:00:00+02:00",

  # время активации кода
  "redeemed_at": null,

  # приватный коментарий кода
  "comment": "Try to activate inside your Plark Wallet",

  # публичный коментарий кода
  "private_comment": "Ripple to the MOON!"
}
```

### Проверить Kuna Code
Единственный публичный метод для Kuna Code. \
Этот метод позволяет проверить доступность Куна кода по его первому сегменту, а так-же узнать валюту, сумму, использован он или еще нет. Метод вернет [API объект Kuna Code].

```bash
GET /v3/kuna_codes/{code}/check
```

**Параметры пути**

| Параметр                | Описание                            |
|-------------------------|-------------------------------------|
| `code` (string)         | 5 первых символов Kuna Code.        |


### Создать Kuna Code
Можно создать Kuna Code с помощью этого метода. Через API можно указать Kuna ID получателя, дату, до которой код не будет доступен создателю на активацию, публичную и приватную заметку.

```bash
POST /v3/auth/kuna_codes
```

**Параметры запроса**

| Параметр                | Обязательный | Описание                            |
|-------------------------|--------------|-------------------------------------|
| `recipient`             | нет          | Получатель кода. По умолчанию код может актировать кто угодно, но если указать Kuna ID, то код сможет ввести только этот аккаунт. |
| `amount*`               | да           | Сумма кода                          |
| `currency*`             | да           | Валюта кода                         |
| `non_refundable_before` | нет          | Формат ISO8601. Дата до которой владелец кода не сможет его активировать. |
| `comment`               | нет          | Публичная заметка к коду.           |
| `private_comment`       | нет          | Приватная заметка к коду, которая видна только владельцу кода. |



### Активировать Kuna Code
Этот метод позволяет активировать Kuna Code и зачислить средства на ваш аккаунт.

```bash
PUT /v3/auth/kuna_codes/redeem
```

**Параметры запроса**

| Параметр              | Обязательный | Описание                            |
|-----------------------|--------------|-------------------------------------|
| `code` (string)       | да           | Код вида `857ny-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-XXXXX-KUN-KCode` |

При успешной активации вы получете ответ:

```bash
HTTP/1.1 200 OK
```
А теле ответа будет [API объект Kuna Code].



### Получить информацию о Kuna Code по ID
У любого кунакода есть уникальный номер. Этот метод позволяет получить информацию о Kuna Code по этому номеру. Метод вернет [API объект Kuna Code].

```bash
POST /v3/auth/kuna_codes/details
```

**Параметры запроса**

| Параметр              | Обязательный | Описание                            |
|-----------------------|--------------|-------------------------------------|
| id (int32)            | да           | Внутренний ID кода                  |

⚠️ Если Kuna Code не пренадлежит вам, то в ответ вы получете ошибку \
`HTTP/1.1 404 Not Found`


### Список выпущенных кодов
С помощью этого метода можно получить список кодов, которые были выпущенны с вашего аккаунта. Метод вернет список объектов, описанных в разделе [API объект Kuna Code].

```bash
POST /v3/auth/kuna_codes/issued-by-me
```

**Параметры запроса**

| Параметр              | Обязательный | Описание                            |
|-----------------------|--------------|-------------------------------------|
| `page` (int32)        | нет          | Номер страницы (по умолчанию 1)     |
| `per_page` (int32)    | нет          | Количество кодов на страницу (по умолчанию 10) |
| `order_by` (string)   | нет          | Сортировать по `created_at`, `redeemed_at`, `amount`  (по умолчанию `created_at`) |
| `order_dir` (string)  | нет          | Порядок сортировки `asc` или `desc` (по умолчанию `desc`) |
| `status` (string[])   | нет          | Фильтровать по статусам `created`, `processing`, `active`, `redeeming`, `redeemed`, `onhold`, `canceled` |



### Список активированных кодов
С помощью этого метода можно получить список кодов, которые были активированы и средства были зачисленны на ваш аккаунт. Метод вернет список объектов, описанных в разделе [API объект Kuna Code].

```bash
POST /v3/auth/kuna_codes/redeemed-by-me
```

**Параметры запроса**

| Параметр               | Обязательный | Описание                            |
|------------------------|--------------|-------------------------------------|
| `page` (int32)         | нет          | Номер страницы (по умолчанию 1)     |
| `per_page` (int32)     | нет          | Количество кодов на страницу (по умолчанию 10) |
| `order_by` (string)    | нет          | Сортировать по `created_at`, `redeemed_at`, `amount`  (по умолчанию `redeemed_at`) |
| `order_dir` (string)   | нет          | Порядок сортировки `asc` или `desc` (по умолчанию `desc`) |

