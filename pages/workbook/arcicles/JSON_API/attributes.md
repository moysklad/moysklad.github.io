---
title: Дополнительные поля
tags: [getting_started, api]
keywords:
summary:
sidebar: workbook_sidebar
permalink: /workbook/workbook/api/remap/1.1/ru/attributes.html
folder: workbook
---
Если вы хотите сохранить информацию, для которой нет подходящего поля в документе или справочнике, вы можете создать дополнительные поля.

### Список сущностей
Список сущностей, для которых есть возможность создать доп. поля, вы можете посмотреть в [документации](https://online.moysklad.ru/api/remap/1.1/doc/index.html#header-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0-%D1%81-%D0%B4%D0%BE%D0%BF%D0%BE%D0%BB%D0%BD%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC%D0%B8-%D0%BF%D0%BE%D0%BB%D1%8F%D0%BC%D0%B8){:target="_blank"}

### Работа с дополнительными полями в АПИ
В рамках JSON API нельзя создавать дополнительные поля, но можно работать с уже созданными через основной интерфейс полями.

### Получение доп. полей
Запросить список доступных полей можно, воспользовавшись запросом метаданных необходимой вам сущности. Ниже приведен пример запроса метаданных товаров, в поле **attributes** выводится массив дополнительных полей:

```shell
curl \
    -X GET \
    -u login:password \
    -H "Lognex-Pretty-Print-JSON: true" \
    "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata"
```

Результат:
```json
{
    "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata",
        "mediaType": "application/json"
    },
    "attributes": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a2",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Особенности",
            "type": "string",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a3",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Объем накопителя",
            "type": "number",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a3",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Дата поступления на склад",
            "type": "time",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/46908d10-c4e5-11e8-9109-f8fc00209552",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "customEntityMeta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/companysettings/metadata/customEntities/9e690967-1703-4038-a8f7-95ef64d54ae6",
                "type": "customentitymetadata",
                "mediaType": "application/json"
            },
            "id": "46908d10-c4e5-11e8-9109-f8fc00209552",
            "name": "Материал изготовления",
            "type": "customentity",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a3",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Спецификация",
            "type": "file",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a3",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Время работы от аккумулятора",
            "type": "double",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a3",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Подсветка клавиатуры",
            "type": "boolean",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/839ca663-75f7-11e8-9107-5048001126a3",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "839ca663-75f7-11e8-9107-5048001126a2",
            "name": "Описание от производителя",
            "type": "text",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/7385ab6e-ad06-11e8-9ff4-34e80004fb35",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "7385ab6e-ad06-11e8-9ff4-34e80004fb35",
            "name": "Ссылка на интернет-магазин",
            "type": "link",
            "required": false
        }
    ],
    "priceTypes": [
        {
            "name": "Цена продажи"
        }
    ],
    "createShared": true
}
```

### Задание значений доп. полей через АПИ
Задать значение доп. полю можно как при создании объекта, так и при его обновлении.

После того, как выше мы получили идентификаторы дополнительных полей товаров, 
мы можем использовать их при создании новых товаров. 
Так как все доп. поля товара из нашего примера имеют флаг **required=false**, 
т.е. не являются обязательными, то не обязательно задавать значения всем доп. полям:
```shell
curl \
    -X POST \
    -u login:password \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json' \
    https://online.moysklad.ru/api/remap/1.1/entity/product \
    -d '{
        "name": "Ноутбук",
        "vat": 18,
        "effectiveVat": 18,
        "uom": {
        "meta": {
          "href": "https://online.moysklad.ru/api/remap/1.1/entity/uom/19f1edc0-fc42-4001-94cb-c9ec9c62ec10",
          "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/uom/metadata",
          "type": "uom",
          "mediaType": "application/json"
        }
        },
        "minPrice": 50000,
        "buyPrice": {
        "value": 50000,
        "currency": {
          "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/currency/metadata",
            "type": "currency",
            "mediaType": "application/json"
          }
        }
        },
        "salePrices": [
        {
          "value": 100000,
          "currency": {
            "meta": {
              "href": "https://online.moysklad.ru/api/remap/1.1/entity/currency/6314188d-2c7f-11e6-8a84-bae500000055",
              "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/currency/metadata",
              "type": "currency",
              "mediaType": "application/json"
            }
          },
          "priceType": "Цена продажи"
        }
        ],
        "attributes": [
            {
              "id": "839ca663-75f7-11e8-9107-5048001126a2",
              "name": "Время работы от аккумулятора",
              "type": "double",
              "value": 9.6
            },
            {
              "id": "7385ab6e-ad06-11e8-9ff4-34e80004fb35",
              "name": "Ссылка на интернет-магазин",
              "type": "link",
              "value": "https://exmaple.com"
            }
        ]
    }'
```
Для нового товара "Ноутбук" мы указали значения двух доп. полей - 
`Время работы от аккумулятора` и `Ссылка на интернет-магазин`.

При обновлении товара мы можем как обновить уже имеющиеся значения доп. полей, так и задать новые.
```shell
curl \
    -X PUT \
    -u login:password \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json' \
    https://online.moysklad.ru/api/remap/1.1/entity/product/630c578a-cb05-11e8-9109-f8fc0037889a \
    -d '{
  "name": "Ноутбук обновленный",
  "attributes": [
    {
      "id": "839ca663-75f7-11e8-9107-5048001126a2",
      "name": "Время работы от аккумулятора",
      "type": "double",
      "value": 10.6
    },
    {
      "id": "839ca663-75f7-11e8-9107-5048001126a2",
      "name": "Подсветка клавиатуры",
      "type": "boolean",
      "value": "true"
    }
  ]
}'
```
В примере мы обновили значение поля `Время работы от аккумулятора`, проставленное при создании товара, а также задали значение полю `Подсветка клавиатуры` - при создании мы оставили его пустым.

Также для необязательных полей есть возможность обнулить значение поля. Для этого в поле **value** необходимо передать значение **null**.

Если в теле запроса на обновление/создание сущности в массиве доп. полей:

+ Не указаны id каких-либо доп. полей - доп. поля обновлены не будут.
+ Указаны id доп. полей, которым в данной сущности ещё не присвоено значение - соответствующим доп. полям будут присвоены переданные значения.
+ Указаны id доп. полей, которым в данной сущности уже присвоено значение - соответствующим доп. полям будут присвоены новые значения.
+ Указан несуществующий id, которого нет в метаданных сущности - возникнет ошибка.

### Возможные типы доп. полей
С возможными типами доп. полей вы можете ознакомиться в [документации](https://online.moysklad.ru/api/remap/1.1/doc/index.html#header-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0-%D1%81-%D0%B4%D0%BE%D0%BF%D0%BE%D0%BB%D0%BD%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC%D0%B8-%D0%BF%D0%BE%D0%BB%D1%8F%D0%BC%D0%B8){:target="_blank"}.

### Доп. поле типа Файл
Для загрузки значения доп. поля типа файл нужно в поле **value** указать объект следующей структуры:

+ filename - Имя файла `Необходимое`
+ content - Байты файла, закодированные в base64 `Необходимое`

Пример создания товара с доп. полем типа Файл приведен ниже.
Для краткости приведено неполное значение содержимого файла.
```shell
curl \
    -X POST \
    -u login:password \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json' \
    https://online.moysklad.ru/api/remap/1.1/entity/product \
    -d '{
    "name": "Ноутбук",
    "attributes": [
        {
          "id": "839ca663-75f7-11e8-9107-5048001126a3",
          "name": "Спецификация",
          "type": "file",
          "file": {
            "filename": "filename",
            "content": "5cYwMpOmNk5kSVr4YgZGKtXJb/7KpHVLDUawyZrD5Nf0WDhB7mS1I77VcAMqYQ8DkP/1wDLhb0X6b2JO4pdpKA=="
          }
        }
    ]
}'
```
### Доп. поле типа Справочник
Дополнительное поле типа Справочник ссылается на объект определенного справочника. 
Это может быть один из встроенных справочников: 
Товары, Контрагенты, Договоры, Сотрудники, Проекты, Склады. 
Или справочник, созданный пользователем.

Рассмотрим пример работы с доп. полями типа Справочник на примере контрагентов. 
В примере для них задано два дополнительных поля: 
встроенный справочник Проект и пользовательский справочник Регион:
```shell
curl \
    -X GET \
    -u login:password \
    -H "Lognex-Pretty-Print-JSON: true" \
    "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata"
```

Результат:
```json
{
    "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
        "mediaType": "application/json"
    },
    "attributes": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/attributes/cf486cca-d383-11e8-ac12-000a000000d4",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "cf486cca-d383-11e8-ac12-000a000000d4",
            "name": "[Проект]",
            "type": "project",
            "required": false
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/attributes/cf489b7c-d383-11e8-ac12-000a000000d5",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "customEntityMeta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/companysettings/metadata/customEntities/ac120c44-d383-11e8-ac12-000a000000c4",
                "type": "customentitymetadata",
                "mediaType": "application/json"
            },
            "id": "cf489b7c-d383-11e8-ac12-000a000000d5",
            "name": "Регион",
            "type": "customentity",
            "required": false
        }
    ],
    "states": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/states/5b77c63b-d047-11e8-ac12-000b0000006b",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
                "type": "state",
                "mediaType": "application/json"
            },
            "id": "5b77c63b-d047-11e8-ac12-000b0000006b",
            "accountId": "5a0480c9-d047-11e8-ac12-000900000000",
            "name": "Новый",
            "color": 15106326,
            "stateType": "Regular",
            "entityType": "counterparty"
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/states/5b77ddd8-d047-11e8-ac12-000b0000006c",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
                "type": "state",
                "mediaType": "application/json"
            },
            "id": "5b77ddd8-d047-11e8-ac12-000b0000006c",
            "accountId": "5a0480c9-d047-11e8-ac12-000900000000",
            "name": "Выслано предложение",
            "color": 10774205,
            "stateType": "Regular",
            "entityType": "counterparty"
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/states/5b77eb48-d047-11e8-ac12-000b0000006d",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
                "type": "state",
                "mediaType": "application/json"
            },
            "id": "5b77eb48-d047-11e8-ac12-000b0000006d",
            "accountId": "5a0480c9-d047-11e8-ac12-000900000000",
            "name": "Переговоры",
            "color": 40931,
            "stateType": "Regular",
            "entityType": "counterparty"
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/states/5b77f0c9-d047-11e8-ac12-000b0000006e",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
                "type": "state",
                "mediaType": "application/json"
            },
            "id": "5b77f0c9-d047-11e8-ac12-000b0000006e",
            "accountId": "5a0480c9-d047-11e8-ac12-000900000000",
            "name": "Сделка заключена",
            "color": 8825440,
            "stateType": "Successful",
            "entityType": "counterparty"
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/states/5b77f469-d047-11e8-ac12-000b0000006f",
                "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
                "type": "state",
                "mediaType": "application/json"
            },
            "id": "5b77f469-d047-11e8-ac12-000b0000006f",
            "accountId": "5a0480c9-d047-11e8-ac12-000900000000",
            "name": "Сделка не заключена",
            "color": 15280409,
            "stateType": "Unsuccessful",
            "entityType": "counterparty"
        }
    ],
    "createShared": false
}
```

Чтобы задать значение доп. поля типа Справочник 
в поле **value** нужно передать объект, содержащий поле **meta** 
с метаданными объекта, который будет значением доп. поля. 
Создадим контрагента с этими доп. полями:
```shell
curl \
    -X POST \
    -u login:password \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json' \
    https://online.moysklad.ru/api/remap/1.1/entity/counterparty \
    -d '{
    "name": "ООО Восток",
    "attributes": [
        {
            "id": "cf486cca-d383-11e8-ac12-000a000000d4",
            "name": "[Проект]",
            "type": "project",
            "value": {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/entity/project/c5ed49c2-d384-11e8-ac12-000a000000d8",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/project/metadata",
                    "type": "project",
                    "mediaType": "application/json",
                    "uuidHref": "https://online.moysklad.ru/app/#project/edit?id=c5ed49c2-d384-11e8-ac12-000a000000d8"
                }
            }
        },
        {
            "id": "cf489b7c-d383-11e8-ac12-000a000000d5",
            "name": "Регион",
            "type": "customentity",
            "value": {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/entity/customentity/ac120c44-d383-11e8-ac12-000a000000c4/b971966b-d383-11e8-ac12-000a000000ce",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/companysettings/metadata/customEntities/ac120c44-d383-11e8-ac12-000a000000c4",
                    "type": "customentity",
                    "mediaType": "application/json",
                    "uuidHref": "https://online.moysklad.ru/app/#custom_ac120c44-d383-11e8-ac12-000a000000c4/edit?id=b971966b-d383-11e8-ac12-000a000000ce"
                    }
                }
        }
    ]
}'
```
Результат:
```json
{
    "meta": {
        "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/5a5597e3-d385-11e8-ac12-000800000000",
        "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
        "type": "counterparty",
        "mediaType": "application/json",
        "uuidHref": "https://online.moysklad.ru/app/#company/edit?id=5a5597e3-d385-11e8-ac12-000800000000"
    },
    "id": "5a5597e3-d385-11e8-ac12-000800000000",
    "accountId": "5a0480c9-d047-11e8-ac12-000900000000",
    "owner": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/employee/5a929317-d047-11e8-ac12-000b0000002e",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/employee/metadata",
            "type": "employee",
            "mediaType": "application/json",
            "uuidHref": "https://online.moysklad.ru/app/#employee/edit?id=5a929317-d047-11e8-ac12-000b0000002e"
        }
    },
    "shared": false,
    "group": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/group/5a05b13e-d047-11e8-ac12-000900000001",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/group/metadata",
            "type": "group",
            "mediaType": "application/json"
        }
    },
    "version": 0,
    "updated": "2018-10-19 12:57:13",
    "name": "ООО Восток",
    "externalCode": "fN3pbKAWhwfAOiz3MFMsA0",
    "archived": false,
    "created": "2018-10-19 12:57:13",
    "companyType": "legal",
    "attributes": [
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/attributes/cf486cca-d383-11e8-ac12-000a000000d4",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "cf486cca-d383-11e8-ac12-000a000000d4",
            "name": "[Проект]",
            "type": "project",
            "value": {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/entity/project/c5ed49c2-d384-11e8-ac12-000a000000d8",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/project/metadata",
                    "type": "project",
                    "mediaType": "application/json",
                    "uuidHref": "https://online.moysklad.ru/app/#project/edit?id=c5ed49c2-d384-11e8-ac12-000a000000d8"
                },
                "name": "Проект 1"
            }
        },
        {
            "meta": {
                "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/attributes/cf489b7c-d383-11e8-ac12-000a000000d5",
                "type": "attributemetadata",
                "mediaType": "application/json"
            },
            "id": "cf489b7c-d383-11e8-ac12-000a000000d5",
            "name": "Регион",
            "type": "customentity",
            "value": {
                "meta": {
                    "href": "https://online.moysklad.ru/api/remap/1.1/entity/customentity/ac120c44-d383-11e8-ac12-000a000000c4/b971966b-d383-11e8-ac12-000a000000ce",
                    "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/companysettings/metadata/customEntities/ac120c44-d383-11e8-ac12-000a000000c4",
                    "type": "customentity",
                    "mediaType": "application/json",
                    "uuidHref": "https://online.moysklad.ru/app/#custom_ac120c44-d383-11e8-ac12-000a000000c4/edit?id=b971966b-d383-11e8-ac12-000a000000ce"
                },
                "name": "Восточный"
            }
        }
    ],
    "accounts": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/5a5597e3-d385-11e8-ac12-000800000000/accounts",
            "type": "account",
            "mediaType": "application/json",
            "size": 0,
            "limit": 100,
            "offset": 0
        }
    },
    "tags": [],
    "contactpersons": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/5a5597e3-d385-11e8-ac12-000800000000/contactpersons",
            "type": "contactperson",
            "mediaType": "application/json",
            "size": 0,
            "limit": 100,
            "offset": 0
        }
    },
    "notes": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/5a5597e3-d385-11e8-ac12-000800000000/notes",
            "type": "note",
            "mediaType": "application/json",
            "size": 0,
            "limit": 100,
            "offset": 0
        }
    },
    "state": {
        "meta": {
            "href": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata/states/5b77c63b-d047-11e8-ac12-000b0000006b",
            "metadataHref": "https://online.moysklad.ru/api/remap/1.1/entity/counterparty/metadata",
            "type": "state",
            "mediaType": "application/json"
        }
    },
    "salesAmount": 0
}
```
### Фильтрация по значению дополнительного поля
JSON API позволяет осуществлять фильтрацию по значению дополнительного поля. На примере дополнительных полей, приведенных выше, можно отфильтровать все товары, у которых значение доп. поля `Время работы от аккумулятора` больше или равно 5:
```shell
curl \
    -X GET \
    -u login:password \
    -H 'Accept: application/json' \
    -H 'Content-Type: application/json' \
    "https://online.moysklad.ru/api/remap/1.1/entity/product?filter=https://online.moysklad.ru/api/remap/1.1/entity/product/metadata/attributes/630c578a-cb05-11e8-9109-f8fc0037889a%3E%3D5"
```

Для этого нам необходимо в параметре filter указать href доп. поля для фильтрации, знак сравнения (в нашем случае `>=`) и значение. В ответе вернутся все сущности, подходящие под переданный критерий.

### Сортировка по дополнительному полю
Сортировка по доп. полям в данный момент не поддерживается.