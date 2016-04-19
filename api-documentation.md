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

* GET https://fragmenter.net/api/v1/fragments/FEED?user_email=exampleEmail&user_token=exampleToken will return 25 fragments:


```
{
  "data": [
     {
      "id": "134145",
      "type": "fragments",
      "attributes": {
        "body": "some text here...",
        "mood": null,
        "language": "ru",
        "user_name": "Sea",
        "user_id": 18774,
        "favorite_assignment_id": 12345,
        "created_at": "2016-03-13T04:25:41.497Z"
      }
    }
  ]
}
```

###### FEED can be:

1. "all"
2. "own"
3. "best"
4. "good"
5. "favorite"
6. "banned"

Fragments marked as "saved" have favorite_assignment_id set to non-nil value. Use this value to remove the assignment
(see below).

## Get more fragments. For infinite scrolling

* GET https://fragmenter.net/api/v1/fragments/groupID?user_email=exampleEmail&user_token=exampleToken&page=exampleNumber will return 25 fragments on selected page:


```
{
  "data": [
     {
      "id": "134119",
      "type": "fragments",
      "attributes": {
        "body": "some text here...",
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

* GET https://fragmenter.net/api/v1/fragments/groupId?user_email=exampleEmail&user_token=exampleToken&before_id=lastCurrentFragmentID, will return 25 fragments:

```
{
  "data": [
     {
      "id": "134131",
      "type": "fragments",
      "attributes": {
        "body": "some text here...",
        "mood": 0,
        "language": "ru",
        "user_name": "Darth pidor",
        "user_id": 16547,
        "created_at": "2016-03-13T01:19:26.525Z"
      }
    }
  ]
}
```

###### GroupIDs same as in Get fragments call.
###### lastCurrentFragmentID is ID of last of your current fragments



## Report fragment

* POST https://fragmenter.net/api/v1/fragments/exampleFragmentId/mark_inappropriate?user_email=exampleEmail&user_token=exampleToken, with parameters: `{}` will return:


```
{
  "success": true
}
```


## Block User

* POST https://fragmenter.net/api/v1/user_relations?user_email=exampleEmail&user_token=exampleToken, with parameters: `{"user_relation": {"relation_type": "ban", "to_id": "exampleUserId"}}` will return


```
{
  "id": "32870",
  "user_id": 15629,
  "relation_type": "ban",
  "to_id": 19407,
  "created_at": "2016-03-13T05:23:23.400Z",
  "updated_at": "2016-03-13T05:23:23.400Z"
}
```



## Post new fragment

* POST https://fragmenter.net/api/v1/fragments/?user_email=exampleEmail&user_token=exampleToken, with parameters:  `{"fragment":{"body":"fragmentBodyText", "mood": "exampleMood", "visibility": "exampleVisibility"}}` will return:

```
{
  "data": {
      "id": "134152",
      "type": "fragments",
      "attributes": {
        "body": "Test text",
        "mood": 1,
        "language": "en",
        "user_name": "TestUser",
        "user_id": 15629,
        "created_at": "2016-03-13T05:25:35.369Z"
      }
   }
}
```

###### Mood can be from -3 to 3, or null

###### Visibility can be:

1. "pub", means All
2. "prv", means Nobody
3. "prt", means Top

## Saving fragments (bookmarks/favorites)

### Saving a fragment with given ID for current user

    POST https://fragmenter.net/api/v1/favorite_assignments/?user_email=exampleEmail&user_token=exampleToken

Params:

    {
      favorite_assignment:
        {
          fragment_id: 1
        }
      }
    }

Returns:

    {
      "created_at": "2016-04-16T08:38:17.188Z",
      "fragment_id": 1,
      "id": 1,
      "updated_at": "2016-04-16T08:38:17.188Z",
      "user_id": 2
    }
  
    ("id" is a new favorite assignment id)

### Removing bookmark

    DELETE https://fragmenter.net/api/v1/favorite_assignments/ID?user_email=exampleEmail&user_token=exampleToken

... where ID is taken either 1) from "favorite_assignment_id" passed along with a fragment (see above), or 2) as "id" when
bookmarking a fragment.

## Getting time of last user's fragment

###### Fragmenter API don't have specific call to get time of last user's fragment. Use

    GET https://fragmenter.net/api/v1/fragments/own?user_email=exampleEmail&user_token=exampleToken

to receive user's fragments, and take time of last one from it.
