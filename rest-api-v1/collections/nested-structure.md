# Nested structure

### Overview

If you look into Raindrop UI you will notice a sidebar in left corner, where collections are located. Collections itself divided by groups. They useful to create separate sets of collections, for example "Home", "Work", etc.

`Groups` array is a single place where user **root** collection list and order is persisted. Why just not to save order position inside collection item itself? Because collections can be shared and they group and order can vary from user to user.

So to fully recreate sidebar like in our app you need to make 3 separate API calls \(sorry, will be improved in future API updates\):

#### 1. [Get user object](../users/authenticated-user.md#get-user)

It contains groups array with exact collection ID's. Typically this array looks like this:

```javascript
{
  "groups": [
    {
      "title": "Home",
      "hidden": false,
      "sort": 0,
      "collections": [
        8364483,
        8364403,
        66
      ]
    },
    {
      "title": "Work",
      "hidden": false,
      "sort": 1,
      "collections": [
        8492393
      ]
    }
  ]
}
```

{% hint style="warning" %}
Collection ID's listed below is just first level of collections structure! To create full tree of nested collections you need to get child items separately.
{% endhint %}

#### 2. [Get root collections](./#get-root-collections)

#### 3. [Get child collections](./#get-nested-collections)

