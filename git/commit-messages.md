# Commit messages

When writing commit messages, you might find yourself writing simple commit messages like "Added feature x.".

While this may be quick and easy and allow you to push your changes and go back to your task, this will not help future readers of the code fully understand what "feature x" was for and why it was needed in the first place.

This might make it more challenging to later refactor, extend, or even delete code related to that feature.

## What's an alternative?

Adopt a standard commit message that aims to tell the reader:

- What the change is about in broad business terms.
- Why was this change needed?
- How is this change working or affecting other parts of the codebase?

To do so, you might consider a variation of this format:
```
Title describing what the change is about in broad business terms.

Why?
- first reason.
- second reason.
etc...

How?
- first major change.
- second major change.
etc...
```

Here is a sample commit message using this format:
```
Allow adding multiple products per order.

Why?
- The previous implementation was based on the assumption that separate orders had to be made for different products.
- The external Orders API actually allows you to create an order with multiple products within a single request.

How?
- Refactor OrdersController#create to comply with updated API documentation.
- Add tests.
```

## Going one step further

If you find this format works for you, you can use it consistently and load a template that you can simply fill in.

### Here is how to do it

Edit your `~/.gitconfig` file to include the following content:

```
# ~/.gitconfig
[commit]
  template = ~/.gitmessage
```

Touch the `~/.gitmessage` file and add the following content:

```
# ~/.gitmessage


Why?
-

How?
-

```
