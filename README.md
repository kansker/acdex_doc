# acdex crm api

> v1.0.0

# api

## POST 1.Get api token

POST https://crm.acdexpty.io/auth/login

Log in to the api account and password to get the token.

> Body request parameters

```json
{
  "account": "api",
  "pwd": "123"
}
```

### Request parameters

| Parameter |Location| Type   | Required | Field description | Comment |
|-----------|---|--------|----------|-------------------|---------|
| body      |body| object | No       || none              |
| » account |body| string | Yes      | account           |     |
| » pwd     |body| string | Yes      | password          |     |

> Example(for return)

> Fail

```json
{
  "s": 0,
  "m": "Fail"
}
```
> Success
> 
```json
{
  "s": 1,
  "token": "XToken eyJ0eXAiOiJKV1QiLCJyIjoxMDAwMCwiYWxnIjoiSFMyNTYifQ.eyJzdWIiOiJhcGkiLCJqdGkiOiI3ZWEyNDc5N2Q3N2I0ZTEyYTZkZTRhYWEzZjIzZWFkMSIsImlhdCI6MTY1NzM1MTE0NX0.dYrCmiDKyrgxowfQyqwdg45x_ZXjIrRg-geGINAsgD4"
}
```

### Return result

| Status code |Status code meaning| illustrate |data model|
|-------------|---|------------|---|
| 200         |[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)| Success|Inline|

### Return data structure

Status code **200**

|Parameter|Type|Required|Field description| Comment|
|---|---------|---|---|--------------------------------------------------------------------------|
|» s| integer |true|Reply status| 1:success,0:fail                                                         |
|» m| string  |false|Reply message|                                                                      |
|» token| string  ||api token| When calling the function api, it is brought into the header token field |

## POST 2.Client Register

POST https://crm.acdexpty.io/api/acdex/register

Submit user registration information

> Body request parameters

```json
{
  "last_name": "Lin",
  "first_name": "Shi Fan",
  "name_en": "Lin Shi Fan",
  "sex": "M",
  "birth_date": "1978/01/01",
  "country": "Thailand",
  "zip": "115",
  "address": "82 Romklao road, Minburi sub-district, Minburi district",
  "city": "Min Buri",
  "pic_government": "/9j/4AAQSkZJRgABAQEAYABgAAD/2wBDAAIBAQIBAQICAgICAgICAwUDAwMDAwYEBAMFBwYHBwcGBwcICQsJCAgKCAcHCg0KCgsMDAwMBwkODw0MDgsMDAz/2wBDAQICAgMDAwYDAwYMCAcIDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAz/wAARCAAuAC8DASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD8BdP0+fVr+G1tYJbm5uZFihhiQvJK7HCqqjkkkgADrmui+J/wY8T/AAZv7W38S6TLpkl7GZICZEljlAOGw6My5HGVzkblJGGGcPw/rt14X16y1Oxl8i9064jureTaG8uRGDK2CCDggHBBFfengjxNof7dH7O1zZ6kmnRav5Zju4UDSHSbsBhFcIpKtg/fGGwQXjLNh68XNsyq4KUKrjek3aT6rt8v+G0P1nw04By3i2ji8vjiHTzCMeahF2VOol8UW3rzbWs1ZXlaSUrfn/RXRfFP4Waz8G/GdzoeuW3kXcHzI65MVzGSdssbYG5Dg89QQQQGBA52vXp1I1IqcHdM/MMbgsRg8RPC4qDhUg2pRas01umu4UUUVZyhXRfCz4p6z8HPGdtrmh3PkXcHyujAmK5jJG6KRcjchwOOoIBBDAEc7RUVKcakXCaumdWCxuIweIhisLNwqQacZJ2aa2afc/QD4n+DfD/7dfwLtb3QL+KK8t5DNYzzRr5lpOFw9tOACyA5XdtPaNxvUKG+EPFvhLUvAniS80jV7OWw1Gwk8ueCQcoeo5HBBBBDAkEEEEgg1137Ofx51L4BfEK31G3mlOlXMiR6raKu8XUAbnCkgeYoLFGyME4J2swP0H+3H4A8G/EX4RQfE7R9QtEvZPJjimhIC60rME8tlOD50YDHpuCxOrD5Rs+VwftMqxKwc7yozfuvs30f9eemp/RvFEsD4j5BV4nwyjSzPBxviIcyUatKK/iQT6rT/wBIbk/Z3+PaKKK+tP5oCiiigAooooAKKKKAP//Z",
  "pic_idcard": "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",
  "pic_bank": "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",
  "passport_id": "1212121",
  "leverage": 100,
  "bank_account": "11100001",
  "bank_name": "Test Bank",
  "live_country": "Thailand",
  "mobile1": "66",
  "mobile2": "611234567",
  "email": "test@test.com",
  "ib_id": 9998
}
```

### Request parameters

| Parameter |Location| Type   | Required | Field description | Comment |
|---|---|---|----------|---|---|
|token|header|string| Yes      ||api token|
|body|body|object| No        |||
|» last_name|body|string| Yes      | Last Name||
|» first_name|body|string| Yes      | First Name||
|» name_en|body|string| Yes      | English name|English name (Passport Name)|
|» sex|body|string| Yes      | Sex|M:Male,F:Female|
|» passport_id|body|string| Yes      | Passport or ID Card No||
|» birth_date|body|string| Yes      | Date of Birth|Format: 1978/01/01|
|» country|body|string| Yes      | Country of Citizenship|Format: English, Example: Thailand|
|» live_country|body|string| Yes      | Country of Residence|Format: English, Example: Thailand|
|» zip|body|string| Yes      | Zip code||
|» city|body|string| Yes      | City||
|» address|body|string| Yes      | Address||
|» mobile1|body|string| Yes      | Mobile Country Code||
|» mobile2|body|string| Yes      | Mobile Number||
|» email|body|string| Yes      | Email Address||
|» ib_id|body|integer| No       | IB ID|Example:9998|
|» leverage|body|integer| Yes      | leverage|100/500|
|» bank_account|body|string| Yes      | Bank account||
|» bank_name|body|string| Yes      | Bank name||
|» pic_government|body|string| Yes      | Government Photo ID|base64 format|
|» pic_idcard|body|string| Yes      | Taking a picture with clients ID card, bank book and the face|base64 format|
|» pic_bank|body|string| Yes      | Bank book picture|base64 format|

> Example(for return)

> Success

```json
{
  "s": 1,
  "m": "Submit completed"
}
```
> Fail
```json
{
  "s": 0,
  "m": "Repeated submit"
}
```

### Return result

| Status code |Status code meaning| illustrate |data model|
|---|---|------------|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)| Success    |Inline|

### Return data structure

Status code **200**

|Parameter|Type|Required|Field description| Comment          |
|---|---|---|---|------------------|
|» s|integer|true|Reply status| 1:success,0:Fail |
|» m|string|false|Reply message|              |
