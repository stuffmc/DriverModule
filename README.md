# Your `#if __has_feature(modules)`: `@import` or not?

### When it works...

I made a sample use of `.modulemap` at [https://github.com/stuffmc/ModuleApp](). You might want to clone it.

It works, and if you peak in `ModuleFramework-Swift.h` you'll see

```objc
#if __has_feature(modules)
#endif
```

### When it doesn't...

Sadly, when I went to apply this in my actual project, I had an error, so I sampled down my project to this sample project.

If all goes well (I mean, _bad_...), when you clone and compile the project here you should see

##### `DriverModule-Swift.h:166:9: Module 'DriverPrivate' not found`

That line points here:

```objc
#if __has_feature(modules)
@import DriverPrivate;
#endif
```

Besides the fact that it really should find `DriverPrivate`, I've been scratching my head to understand, first of all, in what conditions a Framework inserts this `@import` or not. I've been comparing `ModuleFramework` and `DriverModule`... Nothing :(

Do you have the answer? Let me know!