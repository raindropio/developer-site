# Collection groups

### Overview

If you look into Raindrop UI you will notice a sidebar in left corner, where collections are located. Collections itself divided by groups. They useful to create separate sets of collections, for example "Home", "Work", etc.

`Groups` array is a single place where user **root** collection list and order is persisted. Why just not to save order position inside collection item itself? Because collections can be shared and they group and order can vary from user to user.

Typically groups array looks like this:

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

### Group object fields

| Field | Type | Description |
| :--- | :--- | :--- |
| title | `String` | Name of group |
| hidden | `Boolean` | Does group is collapsed |
| sort | `Integer` | Ascending order position |
| collections | `Array<Integer>` | Collection ID's in order |

