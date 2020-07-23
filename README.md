# requ

Requ-js is a simple library for handle client side http requests. It is a wrapper over axios, but with a human touch.
It works as builder, building the endpoint along you go.
At the moment requ-js comes with very few functions.


## we start building our api with

```
this.request() // sort of like init
```

## adding our destination

```
// .to(routeName, [routeParams])

this.request().to('articles',[authorID,articleID]) // imagine our route /articles/{authorid}/articles/{articlesID}
```

## adding extra data we might want to send

```
let data = {
  secret_key: 'super-secret-mon-key'
}

//or

let data = new FormData
data.append('secret_key','you_know_it')

this.request()
  .to(...)
  .with(data)
```
## adding additional headers
Keep building and add on with ".headers()"

```
...
.headers({ 'Accept': 'application/json'})
```

###
the , catch and finally or success, error, endsWith! All of them gives us a callback with the response data, and more!

```
...
 .success((res) => {
      console.log('from-outer-layer',res)
   })
   .error((response,errorBag) => {
     console.log('from-outer-layer-error',response,errorBag)
   })
   .endsWith(() => {
     console.log('from-outer-layer-finally')
     this.loading = false
  })
```

## we have built our request step by step, now to simply send it throug.

```
this.request()
  .to('test',[1,'some-slug'])
  .with(data)
  .headers({ 'test': 'value' })
  .success((res) => {
      console.log('from-outer-layer',res)
   })
   .error((response,errorBag) => {
     console.log('from-outer-layer-error',response,errorBag)
   })
   .endsWith(() => {
     console.log('from-outer-layer-finally')
     this.loading = false
  })
  .send()
```
** incomplete & more features to come**