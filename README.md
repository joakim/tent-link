**This is a suggestion for a new post type, it does not yet exist. WIP. See [Thoughts](#thoughts) for more.**

See also my suggestion for the related [Share](https://github.com/joakim/tent-share) post type.

# Link

A simple Tent post type for sharing/referencing a URL, typically to a web page.

Posts of other types may reference `link` posts for use in the context of that post.

Some examples:

- A [share](https://github.com/joakim/tent-share) post could have only a `message` field and reference the `link` post that has the URL.
- A `bookmark` post could reference a `link` post and provide metadata in its own fields.
- A [status](https://tent.io/docs/post-types#status) post could reference a `link` post for sharing in a conversation. This would be an alternative to adding the URL inline in the `text` field of the `status` post.

In these examples, you'd have to create two posts; first the `link` itself and then the parent post (`share`/`bookmark`/`status`). Tent servers will return any referenced posts as part of the return data for a queried post, so the `link` post would be included when a `share` post is retrieved.

#### Schema

| Property | Required | Type | Description |
| -------- | -------- | ---- | ----------- |
| `url` | Required | String | The URL, obviously. |

#### Example

```json
{
  "content": {
    "url": "http://www.theatlantic.com/technology/archive/2012/10/dark-social-we-have-the-whole-history-of-the-web-wrong/263523/",
  }
}
```

# Thoughts

What would be best – a minimal, generic `link` post ref'd by other posts, such as `bookmark`, `share`, `status`, `whatever`? Or specific post types for each use case, with a `url` field? Maybe this depends on the use case?

Having the link as its own post opens up for metadata about that link to be stored alongside it. It also allows for reuse of the link, although I'm not sure there's any value in that.

Questions:

- What's the performance and storage cost of using refs a lot?
- Wouldn't a side effect of a generic `link` type be that if you subscribed to someone's `link` posts, you'd get anything from `bookmark` links to `share` links to links referenced by `anything`, without the context? Maybe this really isn't an issue, and people would only subscribe to `share` and `bookmark` directly.
- (crazy brainstorming impulse) Could web links even be part of the [post schema](https://tent.io/docs/posts#post-schema), on the same level as refs, mentions and attachments?

Make sure to also see my suggestion for a [Share](https://github.com/joakim/tent-share) post type.
