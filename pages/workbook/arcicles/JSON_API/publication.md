---
title: Публикация документов, особенности работы со ссылками на файлы
tags: []
keywords:
summary:
sidebar: workbook_sidebar
permalink: publication.html
folder: workbook
---
# Публикация документов
МойСклад позволяет печатать документы - формировать файлы в формате _pdf_ или _xls_ по специальным шаблонам, которые называются шаблонами печатных форм. Для большинства документов есть встроенные шаблоны, о создании собственных шаблонов можно прочитать в [статье поддержки](https://support.moysklad.ru/hc/ru/articles/219361888).

Публикация - это ссылка на печатную форму документа. Ее можно отправить по электронной почте. При публикации файлы формируются только в формате _pdf_. Публикации доступны для следующих видов документов:

+ Заказ покупателя
+ Счет покупателю
+ Отгрузка
+ Заказ поставщику
+ Счет поставщика
+ Приемка
+ Входящий платеж
+ Приходный ордер
+ Исходящий платеж
+ Расходный ордер
+ Внутренний заказ
+ Перемещение
+ Оприходование
+ Списание
+ Счет-фактура выданный
+ Счет-фактура полученный
+ Возврат поставщику
+ Возврат покупателя
+ Выплата денег
+ Внесение денег
+ Розничный возврат
+ Розничная продажа
+ Договор

## Создание публикаций в JSON API

Создание публикаций возможно средствами JSON API. Чтобы создать публикацию нужен документ, например, заказ покупателя, и [шаблон печатной формы](#шаблоны-печатной-формы) - встроенный или пользовательский.

Создадим публикацию для заказа покупателя

``` shell
curl 
    -X PUT 
    -u login:password 
    -H "Content-Type: application/json" 
    -H "Lognex-Pretty-Print-JSON: true" 
    "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/53e988fd-c7c9-11e8-9dd2-f3a3000000cd/publication" 
    -d '{
          "template": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/embeddedtemplate/6ffea5e5-1b69-4a88-be59-4856281d439c",
              "type": "embeddedtemplate",
              "mediaType": "application/json"
            }
          }
        }'
```

В ответ возвращается JSON представление публикации. Если такая публикация уже существовала, код ответа 200. Если публикация была создана - 201.
```json
{
  "meta": {
    "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/53e988fd-c7c9-11e8-9dd2-f3a3000000cd/publication/aec51463-bbd2-11e6-8a84-bae500000003",
    "type": "operationpublication",
    "mediaType": "application/json"
  },
  "template": {
    "meta": {
      "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/embeddedtemplate/6ffea5e5-1b69-4a88-be59-4856281d439c",
      "type": "embeddedtemplate",
      "mediaType": "application/json"
    }
  },
  "href": "https://doc.moysklad.ru/board/ef371086-c7c8-11e8-9dd2-f3a300000000/publication/aec51463-bbd2-11e6-8a84-bae500000003.html"
}
```

## Ссылки публикаций

По ссылке публикации (например, https://doc.moysklad.ru/board/ef371086-c7c8-11e8-9dd2-f3a300000000/publication/aec51463-bbd2-11e6-8a84-bae500000003.html) открывается страница, с которой можно скачать pdf-документ. 

 ![useful image]({{ site.url }}/images/publication/publication_download.png)
 
По ссылке будет доступна самая последняя версия документа, даже если вы вносите изменения в документ после его отправки.

Ссылка будет доступна, пока не удалена публикация.

Удалим созданную публикацию заказа покупателя. Сначала запросим список всех публикаций:
``` shell
curl 
    -X GET 
    -u login:password 
    -H "Lognex-Pretty-Print-JSON: true" 
    "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/53e988fd-c7c9-11e8-9dd2-f3a3000000cd/publication" 
```
Ответ:
```json
{
    "context": {
        "employee": {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/context/employee",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/employee/metadata",
                "type": "employee",
                "mediaType": "application/json"
            }
        }
    },
    "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/53e988fd-c7c9-11e8-9dd2-f3a3000000cd/publication",
        "type": "demand",
        "mediaType": "application/json",
        "size": 1,
        "limit": 25,
        "offset": 0
    },
    "rows": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/53e988fd-c7c9-11e8-9dd2-f3a3000000cd/publication/aec51463-bbd2-11e6-8a84-bae500000003",
                "type": "operationpublication",
                "mediaType": "application/json"
            },
            "template": {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/embeddedtemplate/6ffea5e5-1b69-4a88-be59-4856281d439c",
                    "type": "embeddedtemplate",
                    "mediaType": "application/json"
                }
            },
            "href": "https://doc.moysklad.ru/board/45eb22e0-0e7b-11e2-1c31-3c4a92f3a0a7/publication/242ce894-b0fc-4090-a4bd-2ddd1e2a910b.html"
        }
    ]
}
```
Запрос на удаление публикации
``` shell
curl 
    -X DELETE 
    -u login:password 
    -H "Content-Type: application/json" 
    -H "Lognex-Pretty-Print-JSON: true" 
    ""https://online.moysklad.ru/api/remap/1.1/entity/customerorder/53e988fd-c7c9-11e8-9dd2-f3a3000000cd/publication/aec51463-bbd2-11e6-8a84-bae500000003"
```


## Шаблоны печатной формы

В JSON API возможно запросить списки встроенных и пользовательских шаблонов печатных форм, чтобы впоследствии использовать их для печати и публикации документов. 

Запрос встроенных шаблонов заказов покупателей:
``` shell
curl 
    -X GET 
    -u login:password 
    -H "Lognex-Pretty-Print-JSON: true" 
    "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/embeddedtemplate/"
```
Ответ
```json
{
    "context": {
        "employee": {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/context/employee",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/employee/metadata",
                "type": "employee",
                "mediaType": "application/json"
            }
        }
    },
    "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/embeddedtemplate/",
        "type": "embeddedtemplate",
        "mediaType": "application/json",
        "size": 1,
        "limit": 25,
        "offset": 0
    },
    "rows": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/embeddedtemplate/6ffea5e5-1b69-4a88-be59-4856281d439c",
                "type": "embeddedtemplate",
                "mediaType": "application/json"
            },
            "id": "6ffea5e5-1b69-4a88-be59-4856281d439c",
            "name": "Заказ",
            "type": "entity",
            "content": "https://online.moysklad.ru/api/remap/1.1/download-template/order.xls"
        }
    ]
}
```

Запрос пользовательских шаблонов заказов покупателей:
``` shell
curl 
    -X GET 
    -u login:password 
    -H "Lognex-Pretty-Print-JSON: true" 
    "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/customtemplate/"
```
Ответ
```json
{
    "context": {
            "employee": {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/context/employee",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/employee/metadata",
                    "type": "employee",
                    "mediaType": "application/json"
                }
            }
        },
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/customtemplate/",
            "type": "customtemplate",
            "mediaType": "application/json",
            "size": 1,
            "limit": 25,
            "offset": 0
        },
        "rows": [
            {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/entity/customerorder/metadata/customtemplate/13b49a38-0b64-4129-9fb8-0f9f936fa575",
                    "type": "customtemplate",
                    "mediaType": "application/json"
                },
                "id": "13b49a38-0b64-4129-9fb8-0f9f936fa575",
                "name": "order_upakovka.xls",
                "type": "entity",
                "content": "https://online.moysklad.ru/api/remap/1.1/download/13b49a38-0b64-4129-9fb8-0f9f936fa575"
            }
    ]
}
```

По ссылке из поля *content* можно скачать сам шаблон. 

Изменение или удаление шаблонов печатных форм через JSON API невозможно.