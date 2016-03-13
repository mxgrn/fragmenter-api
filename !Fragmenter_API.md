## Authorization 

* POST https://fragmenter.net/api/v1/authenticate, with parameters: `{"email": "examplemail@yahoo.com", "password": "examplePassword"}` will return:


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

* GET https://fragmenter.net/api/v1/fragments/"groupID"?user_email="userEmail"&user_token="userToken" will return 25 fragments:


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

###### GroupID can be:
1. "all"
2. "own"
3. "top"
4. "interesting"
5. "favorite"
6. "banned"


## Get more fragments

* GET https://fragmenter.net/api/v1/fragments/(groupID)?user_email=(userEmail)&user_token=(userToken)&page=(pageNumber) will return 25 fragments on selected page:


```
{
  "data":  [
     {
      "id": "134119",
      "type": "fragments",
      "attributes":  {
        "body": "через месяц уедет Б, еще через месяц приедут предки, а месяц спустя начнется сессия. фантастика. а февраль вышел что надо.\nзато сейчас тепло и ночью так классно пахнет воздух - лучшее время суток.\nжизнь последнее время так прикольно меняется.\nесть радостное желание съесть морковку.\nмяу",
        "mood": null,
        "language": "ru",
        "user_name": "михаль север",
        "user_id": 19461,
        "created_at": "2016-03-12T23:16:51.068Z"
      }
    }
	]
}
``` 

###### GroupIDs same as in Get fragments call.


## Report fragment 

* POST https://fragmenter.net/api/v1/fragments/(fragmentId)/mark_inappropriate?user_email=(userEmail)&user_token=(userToken), with parameters: `{}` will return:


```
{
  "success": true
}
``` 


## Block User

* POST https://fragmenter.net/api/v1/user_relations?user_email=(userEmail)&user_token=(userToken), with parameters: `{"user_relation": {"relation_type": "ban", "to_id": (userId)}}` will return


```
{
    "created_at" = "2016-03-13T05:23:23.400Z";
    id = 32870;
    "relation_type" = ban;
    "to_id" = 19407;
    "updated_at" = "2016-03-13T05:23:23.400Z";
    "user_id" = 15629;
}
``` 



## Send new fragment

* POST https://fragmenter.net/api/v1/fragments/?user_email=(userEmail)&user_token=(userToken), with parameters:  `{"fragment":{"body":(fragmentBodyText), "mood":(mood), "visibility": (visibility)}}` will return:

```
{
    data =     {
        attributes =         {
            body = T;
            "created_at" = "2016-03-13T05:25:35.369Z";
            language = en;
            mood = 1;
            "user_id" = 15629;
            "user_name" = TestUser;
        };
        id = 134152;
        type = fragments;
    };
}
``` 

###### Mood can be from -3 to 3, or null

###### Visibility can be:

1. "pub", means All
2. "prv", means Nobody
3. "prt", means Top









