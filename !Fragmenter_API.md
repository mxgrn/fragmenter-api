## Authorization 

* POST https://fragmenter.net/api/v1/authenticate with parameters `{"email": "examplemail@yahoo.com", "password": "examplePassword"}` will return:


HTTP/1.1 200 OK
X-Runtime:
0.097324
ETag:
"01ea343088f7c50997ff92884d45b385"
X-XSS-Protection:
1; mode=block
X-Request-Id:
b73c6031-2a64-4176-b04c-5d1e0a9b56fa
Connection:
keep-alive
Server:
nginx/1.8.0 + Phusion Passenger 5.0.21
X-Powered-By:
Phusion Passenger 5.0.21
X-Content-Type-Options:
nosniff
Cache-Control:
max-age=0, private, must-revalidate
Status:
200 OK
X-Frame-Options:
SAMEORIGIN
Strict-Transport-Security:
max-age=31536000
Date:
Sun, 13 Mar 2016 04:23:16 GMT
Transfer-Encoding:
chunked
Content-Type:
application/json; charset=utf-8



```
{
  "id": 15629,
  "email": "examplemail@yahoo.com",
  "created_at": "2015-09-17T05:42:30.999Z",
  "updated_at": "2016-02-04T05:04:04.557Z",
  "name": "TestUser",
  "role": "user",
  "active": true,
  "info": "",
  "uid_facebook": null,
  "url_facebook": null,
  "uid_vkontakte": null,
  "url_vkontakte": null,
  "can_login_with_email": true,
  "settings": null,
  "last_active_at": "2015-09-17T05:49:41.670Z",
  "referrer_id": null,
  "referral_token": "DAI3m91yZAIqPaX4qcD-2A",
  "last_seen_pinned_id": null,
  "language": null,
  "authentication_token": "Z9tvm5kDR7ot_Up4nwGF"
}
```