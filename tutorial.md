# Lucky Framework Tutorial

Following the [Lucky Framework Beginner's Tutorial](https://luckyframework.org/guides/tutorial).

## Commands History

### Create the *Fortune* model

```sh
lucky gen.resource.browser Fortune text:String
lucky db.migrate
```

### Associating Models

See [here](https://luckyframework.org/guides/tutorial/associations).

```sh
lucky gen.migration AddBelongsToUserForFortune
lucky db.migrate
```
