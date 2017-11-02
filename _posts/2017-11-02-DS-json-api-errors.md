---
author: Jason Davis
layout: post
title: DS.RESTAdapter and DS.InvalidError
---
My win for the day: I finally tackled why when returning valid json api errors to ember-data RESTAdapter didn't populate errors on the model.

Even though source is not required by json api the RESTAdapter seems to [ignore](https://github.com/emberjs/data/issues/3524#issuecomment-120771056) the message if a source isn't set.

#### PHP formatted error before json encoding:
(this makes me appreciate the php short array syntax)
```php
['errors' => [
    [
        'detail' => $message,
        'source' => ['pointer' => '/data/attributes/id']
    ]
]]
```

#### Now when the adapter error is caught errors.messages should be populated
(we can send more than one error from the backend and access them all)
```js
        save(model) {
            let toast = this.get('toast');
            model.save()
                .then(() => {
                    toast.success('Event Changes Saved');
                })
                .catch(() => {
                    if (model.get('errors.messages.length') > 0) {
                        model.get('errors.messages').forEach((message) => {
                            toast.error(message);
                        });
                    } else {
                        toast.error('Failed to Save');
                    }
                });
        }
```
#### We can also get the error messages in the template
```hbs
{{#each model.errors.messages as |error|}}
  <div class="error">
    {{error}}
  </div>
{{/each}}
```
