# instagram-nodejs

#### Auth and get followers on instagram with nodejs

#### License - BSD-3-Clause
#### Important : you must update csrf token and sessionId only if password was changed

#### To install from npm repository (I recommended use yarn, but you can use npm):
```
yarn add instagram-nodejs-without-api
```

#### You can get instagram followers with next code:
```js
Instagram = new Instagram()


Instagram.getCsrfToken().then((csrf) =>
{
  Instagram.csrfToken = csrf;
}).then(() =>
{
  Instagram.auth('inst-your-username', 'inst-your-password').then(sessionId =>
  {
    Instagram.sessionId = sessionId

    Instagram.getUserDataByUsername('username-for-get').then((t) =>
    {
      Instagram.getUserFollowers(JSON.parse(t).user.id).then((t) =>
      {
        console.log(t); // - instagram followers for user "username-for-get"
      })
    })

  })
})
```

### Follow/unfollow
```js
Inst = new Instagram()

Inst.csrfToken = 'your-csrf'
Inst.sessionId = 'your-session-id'
Inst.follow(3,0) //follow "kevin"
Inst.follow(3, 1) //unfollow "kevin"
````

### User data (username,profile pic,full name) by id or name
```js
	Inst.csrfToken = 'your-csrf'
	Inst.sessionId = 'your-session-id'
	let userById = Inst.getUserDataById(3) //get user data for "kevin"
	let userByUsername = Inst.getUserDataByUsername("kevin") // get user data by username
	console.log(userById.username) // kevin
```

Star this repository on github, please. Thank you
