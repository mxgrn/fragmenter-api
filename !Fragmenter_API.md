## Authorization 

* POST https://fragmenter.net/api/v1/authenticate with parameters `{"email": "examplemail@yahoo.com", "password": "examplePassword"}` will return:


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

###### You want to save "authentication_token" and "email", later you will need them for the following calls.



## Get fragments

* GET https://fragmenter.net/api/v1/fragments/**groupID**?user_email=**userEmail**&user_token=**userToken**  will return 25 fragments:

###### GroupID can be:
1. "all"
2. "own"
3. "top"
4. "interesting"
5. "favorite"
6. "banned"

```
{
  "data":  [
     {
      "id": "134145",
      "type": "fragments",
      "attributes":  {
        "body": "× Вечером иду в душ и спать. Сплю на боку, так получается. И поэтому пробор съезжает на бок и так и остается. Это иногда дико раздражает, т.к. изменить ничего не получается, а так - прикольно :'D\n× Завтра будет тяжёлый день. До шк - тест по физике, потом кр по физике, всякие проверочные, и после шк - кр по истории. Зато в 3 часа дня уже буду свободна. Хах. Неделя до конца четверти. Я справлюсь.\n× Ощущение лета. Хочется тепла, дождей, зелени. В моем воображении это все уже есть ^ ^ Скоро и в реальности будет. Стоп. Там все еще снег.. Замечталась > <",
        "mood": null,
        "language": "ru",
        "user_name": "Sea",
        "user_id": 18774,
        "created_at": "2016-03-13T04:25:41.497Z"
      }
    }
    ]
}   
``` 