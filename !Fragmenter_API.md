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
        "body": "\U0411\U0440\U043e \U043c\U043d\U0435 \U0441\U043a\U0438\U043d\U0443\U043b\U0430 \U043a\U0443\U0447\U0443 \U0441\U0442\U0430\U0440\U044b\U0445 \U0444\U043e\U0442\U043e\U0433\U0440\U0430\U0444\U0438\U0439. \n\U041d\U043e\U0441\U0442\U0430\U043b\U044c\U0433\U0438\U044f \U043d\U0430\U043a\U0440\U044b\U043b\U0430. \U042f \U0431\U044b\U043b \U0441\U043e\U0432\U0441\U0435\U043c \U0434\U0440\U0443\U0433\U043e\U0439. \n\U041d\U043e\U0441\U0438\U043b \U044d\U0442\U0438 \U0446\U0432\U0435\U0442\U043d\U044b\U0435 \U043b\U0435\U043d\U0442\U044b \U043d\U0430 \U0440\U0443\U043a\U0430\U0445, \U0434\U0440\U0443\U0433\U0438\U0435 \U043e\U0447\U043a\U0438, \U0434\U0440\U0443\U0433\U0430\U044f \U043f\U0440\U0438\U0447\U0451\U0441\U043a\U0430, \U0440\U043e\U0446\U043a \U044d\U0442\U043e\U0442 \U0441\U043b\U0443\U0448\U0430\U043b.\n\U0410 \U0441\U0435\U0439\U0447\U0430\U0441 \U0432\U0441\U0451 \U043d\U0435 \U0442\U0430\U043a..",
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



## Get more fragments. For infinite scrolling

* GET https://fragmenter.net/api/v1/fragments/"groupID"?user_email="userEmail"&user_token="userToken"&page="pageNumber" will return 25 fragments on selected page:


```
{
  "data":  [
     {
      "id": "134119",
      "type": "fragments",
      "attributes":  {
        "body": "\U0411\U0440\U043e \U043c\U043d\U0435 \U0441\U043a\U0438\U043d\U0443\U043b\U0430 \U043a\U0443\U0447\U0443 \U0441\U0442\U0430\U0440\U044b\U0445 \U0444\U043e\U0442\U043e\U0433\U0440\U0430\U0444\U0438\U0439. \n\U041d\U043e\U0441\U0442\U0430\U043b\U044c\U0433\U0438\U044f \U043d\U0430\U043a\U0440\U044b\U043b\U0430. \U042f \U0431\U044b\U043b \U0441\U043e\U0432\U0441\U0435\U043c \U0434\U0440\U0443\U0433\U043e\U0439. \n\U041d\U043e\U0441\U0438\U043b \U044d\U0442\U0438 \U0446\U0432\U0435\U0442\U043d\U044b\U0435 \U043b\U0435\U043d\U0442\U044b \U043d\U0430 \U0440\U0443\U043a\U0430\U0445, \U0434\U0440\U0443\U0433\U0438\U0435 \U043e\U0447\U043a\U0438, \U0434\U0440\U0443\U0433\U0430\U044f \U043f\U0440\U0438\U0447\U0451\U0441\U043a\U0430, \U0440\U043e\U0446\U043a \U044d\U0442\U043e\U0442 \U0441\U043b\U0443\U0448\U0430\U043b.\n\U0410 \U0441\U0435\U0439\U0447\U0430\U0441 \U0432\U0441\U0451 \U043d\U0435 \U0442\U0430\U043a..",
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



## Get fragments before your current 25 fragments. For infinite scrolling

* GET https://fragmenter.net/api/v1/fragments/"groupId"?user_email="email"&user_token="token"&before_id="lastCurrentFragmentID", will return 25 fragments:

```
[{
    attributes =     {
        body = "\U0411\U0440\U043e \U043c\U043d\U0435 \U0441\U043a\U0438\U043d\U0443\U043b\U0430 \U043a\U0443\U0447\U0443 \U0441\U0442\U0430\U0440\U044b\U0445 \U0444\U043e\U0442\U043e\U0433\U0440\U0430\U0444\U0438\U0439. \n\U041d\U043e\U0441\U0442\U0430\U043b\U044c\U0433\U0438\U044f \U043d\U0430\U043a\U0440\U044b\U043b\U0430. \U042f \U0431\U044b\U043b \U0441\U043e\U0432\U0441\U0435\U043c \U0434\U0440\U0443\U0433\U043e\U0439. \n\U041d\U043e\U0441\U0438\U043b \U044d\U0442\U0438 \U0446\U0432\U0435\U0442\U043d\U044b\U0435 \U043b\U0435\U043d\U0442\U044b \U043d\U0430 \U0440\U0443\U043a\U0430\U0445, \U0434\U0440\U0443\U0433\U0438\U0435 \U043e\U0447\U043a\U0438, \U0434\U0440\U0443\U0433\U0430\U044f \U043f\U0440\U0438\U0447\U0451\U0441\U043a\U0430, \U0440\U043e\U0446\U043a \U044d\U0442\U043e\U0442 \U0441\U043b\U0443\U0448\U0430\U043b.\n\U0410 \U0441\U0435\U0439\U0447\U0430\U0441 \U0432\U0441\U0451 \U043d\U0435 \U0442\U0430\U043a..";
        "created_at" = "2016-03-13T01:19:26.525Z";
        language = ru;
        mood = 0;
        "user_id" = 16547;
        "user_name" = "Darth pidor";
    };
    id = 134131;
    type = fragments;
}]
``` 

###### GroupIDs same as in Get fragments call.
###### lastCurrentFragmentID is ID of last of your current fragments



## Report fragment 

* POST https://fragmenter.net/api/v1/fragments/"fragmentId"/mark_inappropriate?user_email="userEmail"&user_token="userToken", with parameters: `{}` will return:


```
{
  "success": true
}
``` 


## Block User

* POST https://fragmenter.net/api/v1/user_relations?user_email="userEmail"&user_token="userToken", with parameters: `{"user_relation": {"relation_type": "ban", "to_id": "userId"}}` will return


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



## Post new fragment

* POST https://fragmenter.net/api/v1/fragments/?user_email="userEmail"&user_token="userToken", with parameters:  `{"fragment":{"body":"fragmentBodyText", "mood":(mood), "visibility": "visibility"}}` will return:

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



## Time of last user's fragment

###### Fragmenter API don't have specific call to get time of last user's fragment. I am using GET https://fragmenter.net/api/v1/fragments/own?user_email="userEmail"&user_token="userToken" and take time of last user's fragment from it.





