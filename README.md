# Link

A simple Tent post type for sharing a URL, typically to a web page.

This is a WIP.

#### Schema

| Property | Required | Type | Description |
| -------- | -------- | ---- | ----------- |
| `url` | Required | String | The URL that is shared. |
| `message` | Optional | String | A short text about this link from the owner of the post. |

#### Example

```json
{
  "content": {
    "url": "http://www.theatlantic.com/technology/archive/2012/10/dark-social-we-have-the-whole-history-of-the-web-wrong/263523/",
    "message": "An interesting article on link sharing, and how most of it happens outside of the traditional social networks."
  }
}
```
