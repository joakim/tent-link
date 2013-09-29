**This is very much a work in progress, and only a suggestion.**

# Link

A simple Tent post type for sharing/referencing a URL, typically to a web page.

Posts of other types may reference `link` posts for use in a particular context.

For example, a [status](https://tent.io/docs/post-types#status) post could reference a `link` for sharing in a conversation (as that is the nature of `status` posts). This would be an alternative to adding the URL inline in the `text` field of the `status` post. It _could_ result in a representation similar to Twitter's cards when rendered. "Cleaner" methinks.

A `share` post could have only a `message` field and reference the `link` post that has the URL (see [this example](#example-1)). A `bookmark` post could reference a `link` and add metadata in its own fields.

In these examples, you'd have to create two posts; first the `link` itself and then the "parent" post (`share`/`bookmark`/`status`). Tent servers will return any referenced posts as part of the return data for a queried post, so the `link` post would be included when a `bookmark` post is retrieved.

#### Schema

| Property | Required | Type | Description |
| -------- | -------- | ---- | ----------- |
| `url` | Required | String | The URL… |

#### Example

```json
{
  //...
  "content": {
    "url": "http://www.theatlantic.com/technology/archive/2012/10/dark-social-we-have-the-whole-history-of-the-web-wrong/263523/",
  }
}
```

#### Thoughts

What would be best – a minimal, generic `link` post ref'd by other posts, such as `bookmark`, `share`, `status`, `whatever`? Or specific post types for each use case, with a `url` field?

- What's the performance and storage cost of using refs a lot?
- Would a side effect of a generic `link` type be that if you subscribe to someone's `link` posts, you'd get anything from `bookmark` links to `share` links to links referenced by `anything`, without the context?
- (brainstorming) Could web links even be part of the [post schema](https://tent.io/docs/posts#post-schema), on the same level as refs, mentions and attachments?

# Share

A shared link.

#### Schema

| Property | Required | Type | Description |
| -------- | -------- | ---- | ----------- |
| `message` | Optional | String | A short text about this link from the owner of the post. |

#### Example

```json
{
  //...
  "content": {
    "message": "An interesting article on link sharing, and how most of it happens outside of the traditional social networks.",
  },
  "refs": [
    {
      //...
    }
  ]
}
```

