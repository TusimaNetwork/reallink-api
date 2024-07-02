# Web2 services are connected to Web3 through Tusima

[日本語版](README.ja.md)

  **v1.0.0**

## Default



#### POST registerweb3account

```
POST  /user/registerweb3account
```

> Register in web3 server and generate bound web3 addresses for users
>



**Body request parameters**

```json
{
  "euserId": 13,
  "euserName": "smithl",
  "email": "r.ngerd@gmail.com",
  "appName": "damai",
  "phone": "18601395213"
 }
```



**Request parameters**

| name        | position | type        | required | explain             | remark                                    |
| ----------- | -------- | ----------- | -------- | ------------------- | ----------------------------------------- |
| body        | body     | object      | no       |                     | none                                      |
| » euserId   | body     | integer     | yes      | External userID     | none                                      |
| » euserName | body     | string      | yes      | External userName   | none                                      |
| » email     | body     | string¦null | yes      | User  email         | At least one email and phone number exist |
| » appName   | body     | string      | yes      | Source channel      | none                                      |
| » phone     | body     | string¦null | yes      | Mobile phone number | At least one email and phone number exist |



**Return example**

success

```json
{
  "code": 0,
  "msg": "",
  "data": {}
 }

{
  "code": 500008,
  "msg": "User-generated web3 address failed",
  "data": {}
 }
```



**Return results**

| condition code | Status code meaning                                     | instruction | data model |
| -------------- | ------------------------------------------------------- | ----------- | ---------- |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success     | Inline     |



**Returns the data structure**

Status code **200**

| name   | type    | required | restrain | explain | remark                      |
| ------ | ------- | -------- | -------- | ------- | --------------------------- |
| » code | integer | true     | none     |         | return code                 |
| » msg  | string  | true     | none     |         | Msg  information            |
| » data | object  | true     | none     |         | Return specific information |



 

#### POST update

```
POST /user/update
```

> Update the user information in the web3server, and the different mobile phone numbers or different mailboxes of different platforms are regarded as different users
>



**Body  required parameter** 

```json
{
  "phone": "18141248869",
  "appName": "damai",
  "euserId": 71
 }
```



**Required parameter** 

| name        | position | type        | required | explain | remark |
| ----------- | -------- | ----------- | -------- | ------- | ------ |
| body        | body     | object      | no       |         | none   |
| » euserName | body     | string¦null | yes      |         | none   |
| » phone     | body     | string¦null | yes      |         | none   |
| » email     | body     | string¦null | yes      |         | none   |
| » appName   | body     | string      | yes      |         | none   |
| » euserId   | body     | integer     | yes      |         | none   |





**Return example**

success

```json
{      
   "code":    0,      
   "msg":    "",      
   "data":    {}     
}    

{      
  "code":    500006,      
  "msg":    "The user does not exist",      
  "data":    {}     
}
```



**Return results**

| condition code | Status code meaning                                     | explain | data model |
| -------------- | ------------------------------------------------------- | ------- | ---------- |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline     |





**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark       |
| ------ | ------- | -------- | -------- | ------- | ------------ |
| » code | integer | true     | none     |         | Message code |
| » msg  | string  | true     | none     |         | information  |
| » data | object  | true     | none     |         | data         |



#### POST delete

```
POST /user/delete
```

> According to email and channel, delete the user, delete as a soft deletion
>



**Body required parameter**

```json
{
  "appName": "damai",
  "euserId": 79
 }
```



**Required parameter**

| name      | position | type    | required | explain           | remark |
| --------- | -------- | ------- | -------- | ----------------- | ------ |
| body      | body     | object  | no       |                   | none   |
| » appName | body     | string  | yes      | irrigation ditch  | none   |
| » euserId | body     | integer | yes      | External users Id | none   |



**Return example**

success

``` json
{
  "code": 0,
  "msg": "",
  "data": {}
 }

{
  "code": 500006,
  "msg": "The user does not exist",
	"data":    {}
}
```



**Return results**

| condition code | Status   code meaning                                   | explain | data   model |
| -------------- | ------------------------------------------------------- | ------- | ------------ |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline       |



**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark |
| ------ | ------- | -------- | -------- | ------- | ------ |
| » code | integer | true     | none     |         | none   |
| » msg  | string  | true     | none     |         | none   |
| » data | object  | true     | none     |         | none   |



#### POST purchasenft

```
POST /order/purchasenft
```

> The app pushes the purchase nft request to the web3 server, and the web3server will initialize the order into the pending state, which will be issued by the web3server backend logic and nft
>



**Body required parameter**

```json
{
  "appName": "damai",
  "nftActivityName": "jackchou ticket",
  "price": 0,
  "amount": 15,
  "euserId": 70, 
  "enftId": 12
}
```



**Required parameter**

| name                | position | type    | required | explain                           | remark |
| ------------------- | -------- | ------- | -------- | --------------------------------- | ------ |
| body                | body     | object  | no       |                                   | none   |
| » appName           | body     | integer | yes      | irrigation ditch                  | none   |
| » nft Activity Name | body     | string  | yes      | Project name of the purchased nft | none   |
| » price             | body     | integer | yes      | price                             | none   |
| » amount            | body     | integer | yes      | purchase quantity                 | none   |
| » euserId           | body     | integer | yes      | External users Id                 | none   |
| » enftId            | body     | integer | yes      | External nft active Id            | none   |



**Return example**

success

```json
{      
  "code":    0,      
  "msg":    "",      
  "data":    ""     
}    

{      
  "code":    600002,      
  "msg":    "When users buy nft, the quantity does    not meet the requirements",      
  "data":    "in consequat"     
} 
```



**Return results**

| condition code | Status   code meaning                                   | remark  | data   model |
| -------------- | ------------------------------------------------------- | ------- | ------------ |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline       |



**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark |
| ------ | ------- | -------- | -------- | ------- | ------ |
| » code | integer | true     | none     |         | none   |
| » msg  | string  | true     | none     |         | none   |
| » data | string  | true     | none     |         | none   |



#### POST login

```
POST /user/login
```

> The web3 login interface, if there is an address, directly return, if there is no web3 address, generate and bind
>
> The web3 address
>



**Body required parameter**

```json
{
  "appName": "damai",
  "euserId": 54
 }
```



 

**Required parameter**

| name      | position | type    | required | explain          | remark |
| --------- | -------- | ------- | -------- | ---------------- | ------ |
| body      | body     | object  | no       |                  | none   |
| » appName | body     | string  | yes      | Channel name     | none   |
| » euserId | body     | integer | yes      | External User Id | none   |



**Return example**

success

```json
{
  "code": 0,
  "msg": "",
  "data": {}
 }

{
  "code": 500008,
  "msg": "User-generated web3 address failed",
  "data": {}
 }
```



**Return results**

| condition code | Status   code meaning                                   | remark  | data   model |
| -------------- | ------------------------------------------------------- | ------- | ------------ |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline       |



**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark |
| ------ | ------- | -------- | -------- | ------- | ------ |
| » code | integer | true     | none     |         | none   |
| » msg  | string  | true     | none     |         | none   |
| » data | object  | true     | none     |         | none   |



#### POST addactivity

```
POST /nft/addactivity
```

> Provide app squares to the ability to increase nft activity
>



**Body required parameter**

```json
{
  "nftActivityName": "jackchou In Concert",
  "imageFileName": "picture.jpg",
  "appName": "damai",
  "enftId": 29,
  "imageFileContent": "Picture base64 encoding"
 }
```



**Required parameter**

| name                 | position | type    | required | explain                  | remark |
| -------------------- | -------- | ------- | -------- | ------------------------ | ------ |
| body                 | body     | object  | no       |                          | none   |
| » nft Activity Name  | body     | string  | yes      | Activity name            | none   |
| » image File Name    | body     | string  | yes      | picture file name        | none   |
| » app Name           | body     | string  | yes      | Channel name             | none   |
| » enft Id            | body     | integer | yes      | External nft active id   | none   |
| » image File Content | body     | string  | yes      | Picture  base64 encoding | none   |



**Return example**

success

```json
{
  "code": 0,
  "msg": "",
  "data": {}
 }

{
  "code": 500008,
  "msg": "The nft activity of the same ID of the same channel already exists",
  "data": {}
 }
```



**Return results**

| condition code | Status   code meaning                                   | remark  | data   model |
| -------------- | ------------------------------------------------------- | ------- | ------------ |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline       |



**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark |
| ------ | ------- | -------- | -------- | ------- | ------ |
| » code | integer | true     | none     |         | none   |
| » msg  | string  | true     | none     |         | none   |
| » data | object  | true     | none     |         | none   |



#### POST update activity

```
POST /nft/updateactivity
```

> Modify the nft activity
>



**Body required parameter**

```json
{
  "nftActivityName": "jackchou ticket",
  "appName": "damai",
  "enftId": 63
 }
```



**Required parameter**

| name               | position | type        | required | explain                   | remark |
| ------------------ | -------- | ----------- | -------- | ------------------------- | ------ |
| body               | body     | object      | no       |                           | none   |
| » nftActivityName  | body     | string¦null | yes      | activity   name           | none   |
| » appName          | body     | string      | yes      | Channel  name             | none   |
| » enftId           | body     | integer     | yes      | External  nft activity ID | none   |
| » imageFileContent | body     | string¦null | yes      | Picture base64 encoding   | none   |



**Return example**

success

```json
{
  "code": 0,
  "msg": "",
  "data": {}
 }

{
  "code": 600001,
  "msg": "The nft activity does not exist",
  "data": {}
 }
```



**Return results**

| condition code | Status   code meaning                                   | remark  | data   model |
| -------------- | ------------------------------------------------------- | ------- | ------------ |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline       |



**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark |
| ------ | ------- | -------- | -------- | ------- | ------ |
| » code | integer | true     | none     |         | none   |
| » msg  | string  | true     | none     |         | none   |
| » data | object  | true     | none     |         | none   |



#### POST delete activity

```
POST /nft/deteteactivity
```

> Delete the nft activity
>



**Body required parameter**

```json
{
  "enftId": 80,
  "appName": "damai"
 }
```



**Required parameter**

| name      | position | type    | required | explain                | remark        |
| --------- | -------- | ------- | -------- | ---------------------- | ------------- |
| body      | body     | object  | no       |                        | none          |
| » enftId  | body     | integer | yes      | External nft active Id | none          |
| » appName | body     | string  | yes      | Channel  name          | Channel  name |



**Return example**

success

```json
{
  "code": 0,
  "msg": "",
  "data": {}
 }

{
  "code": 600001,
  "msg": "The nft activity does not exist",
  "data": {}
 }
```



**Return results**

| condition code | Status   code meaning                                   | explain | data   model |
| -------------- | ------------------------------------------------------- | ------- | ------------ |
| 200            | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | success | Inline       |



**Returns the data structure**

condition code **200**

| name   | type    | required | restrain | explain | remark |
| ------ | ------- | -------- | -------- | ------- | ------ |
| » code | integer | true     | none     |         | none   |
| » msg  | string  | true     | none     |         | none   |
| » data | object  | true     | none     |         | none   |





# Parameter format description

User name , app name ,  Activity name rule:

•     The length should be from 6 to 30 characters. A user name can be any combination of letters, numbers, or symbols

•     Do not include and symbols (&), equal sign (=), underline (_), apostrophe ('), dash (-), plus (+), English comma (,), sharp brackets (<,>) or multiple consecutive points (. ).

•     You can use the divide-point (. ) Non-alphanumeric characters outside as the beginning or end

​      phone : The Japanese mobile phone number rules

​      euserId , enftID : External user ID, External nft active ID is greater than 0



# Error code description

The error message is indicated by code and msg in the returned message. This error code table is constantly being updated, and the information type is as follows：



| code   | msg                                                          |
| ------ | ------------------------------------------------------------ |
| 500001 | The user name format is not compliant                        |
| 500002 | User name length does not meet the requirements              |
| 500003 | The mobile phone number format does not meet the requirements |
| 500004 | The length of the mobile phone number does not meet the  requirements |
| 500005 | The mailbox format does not meet the requirements            |
| 500006 | The user does not exist                                      |
| 500007 | The user already exists                                      |
| 500008 | User-generated web3 address failed                           |
| 600001 | The nft activity does not exist                              |
| 600002 | The nft purchase quantity is not compliant                   |
| 600003 | User failed to place an order                                |
| 600004 | The nft activity of the same ID of the same channel already exists |
| 700001 | The request header auth is empty                             |
| 700002 | Request header auth format error                             |



# Interface security design

Due to the adoption of mainstream RESTful API design methods, it is stateless. If authentication is not done, it will have a significant impact on security. Here are three options to choose from at your discretion

## API authentication scheme

•     Cookie+session method, the most traditional authentication scheme, may be limited in usage scenarios

•     API key+API secret method, generally speaking, each API needs to be assigned a pair of Key and Secret, so when there are many Key and Secret, the server will have a certain storage cost

•     Based on the token mechanism, there are many specific implementation solutions, and the mainstream technology adopts JWT

Other related technical means will be considered to increase interface security during development

•     Add a timestamp to prevent a timeout replay attack

•     Use HTTPS: Prevent the explicit transmission of data

•     Interface rate limit prevents DDOS attacks



# Remark

According to the development situation, this document is in constant adjustment and will be communicated when adjusting
