# Link

A simple Tent post type for sharing/referencing a URL, typically to a web page. **This is a WIP.**

Posts of other types may reference `link` posts for use in a particular context.

For example, a [status](https://tent.io/docs/post-types#status) post could reference a `link` for sharing in/as a conversation (as that is the nature of `status` posts). This would be an alternative to adding the link inline in the `text` field of the `status` post, and could result in a representation similar to Twitter's cards when rendered. "Cleaner" methinks.

#### Schema

| Property | Required | Type | Description |
| -------- | -------- | ---- | ----------- |
| `url` | Required | String | The URL that is shared. |
| `note` | Optional | String | A short text about this link from the owner of the post. |

#### Example

```json
{
  "content": {
    "url": "http://www.theatlantic.com/technology/archive/2012/10/dark-social-we-have-the-whole-history-of-the-web-wrong/263523/",
    "note": "An interesting article on link sharing, and how most of it happens outside of the traditional social networks."
  }
}
```

#### Thoughts

- What's best – a minimal, generic link type ref'd by eg. `bookmark`/`share`/`status`/`anything`? Or specific post types for each case?
- What's the performance and storage cost of using refs a lot?
- Would a side effect of a generic `link` type be that if you subscribe to someone's `link`s, you'd get anything from `bookmark`s to `share`s to _whatever_ is using `link`, without the context?

