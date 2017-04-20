### Content

* [GET `/api/users/{userId}/`](#get-apiusersuserid)
* [GET `/api/users/{userId}/posts/`](#get-apiusersuseridposts)
* [GET `/api/users/{userId}/posts/{postId}/`](#get-apiusersuseridpostspostid)

* [GET `/api/posts/`](#get-apiposts)
* [GET `/api/posts/{postId}/`](#get-apipostspostid)

* [POST `/api/users/`](#post-apiusers)
* [POST `/api/users/{userId}/posts/`](#post-apiusersuseridposts)
* [POST `/api/posts/`](#post-apiposts)


* [DELETE `/api/users/{userId}/`](#delete-apiusersuserid)
* [DELETE `/api/users/{userId}/posts/{postId}/`](#delete-apiusersuseridpostspostid)
* [DELETE `/api/posts/{postId}/`](#delete-apipostspostid)

#### GET `/api/users/{userId}/`

* 描述：获取某用户信息

* 响应成功
  * 状态码
      + 200 OK
  * 响应体样例

``` json
{
  "name": "manley",
  "password":"123456",
  "id": 1,
  "url": "/api/users/1",
  "posts_url": "/api/users/1/posts"
}
```

* 响应失败
  * 状态码
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)

#### GET `/api/users/{userId}/posts/`

* 描述：获取用户提过的问题列表

* 响应成功
  * 状态码
      + 200 OK
  * 响应体样例

``` json
[
  {
    "id": 1911028,
    "url": "/api/posts/1911028",
  },
  {
    "id": 120765,
     "url": "/api/posts/120765",
  },
  ...
]
```

* 响应失败
  * 状态码
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```
[back to Content](#content)

#### GET `/api/users/{userId}/posts/{postId}/`

* 描述：获取用户提过的某个问题

* 响应成功
  * 状态码
      + 200 OK
  * 响应体样例

``` json
[
  {
    "id": 1911028,
    "url": "/api/posts/1911028",
  }
]
```

* 响应失败
  * 状态码
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```
[back to Content](#content)

#### GET `/api/posts/`

* 描述：获取用户提过的问题列表

* 响应成功
  * 状态码
      + 200 OK
  * 响应体样例

``` json
[
  {
    "id": 1911028,
    "content": "如何评价图灵？",
    "label": "早餐",
    "url": "/api/posts/1911028",
  },
  {
    "id": 120765,
    "content": "如何评价唐纳德？",
    "label": "午餐",
    "url": "/api/posts/120765",
  },
  ...
]
```

* 响应失败
  * 状态码
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```
[back to Content](#content)


#### GET `/api/posts/{postId}/`

* 描述：获取用户提过的问题列表

* 响应成功
  * 状态码
      + 200 OK
  * 响应体样例

``` json
[
  {
    "id": 1911028,
    "content": "如何评价图灵？",
    "label": "早餐",
    "url": "/api/posts/1911028",
  }
]
```

* 响应失败
  * 状态码
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```
[back to Content](#content)

#### POST `/api/users/`

* 描述：用户注册时创建一个用户

* 请求
  * 请求体样例

``` json
{
  "name": "manley",
  "password": "qewrtyuasdf",
}
```

* 响应成功
  * 状态码
      + 201 CREATED
  * 响应体样例

``` json
{
  "url": "/api/users/12432"
}
```

* 响应失败
  * 状态码
      + 409 CONFLICT
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "User already exists",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)

#### POST `/api/users/{userId}/posts/`

* 描述：用户发帖

* 请求
  * 请求体参数
      
  * 请求体样例

``` json
{
  "name": "manley",
  "password": "jfljsdfkljdfs"
  "postId":"123456"
}
```

* 响应成功
  * 状态码
        + 201 CREATED
``` json
{
  "url": "/api/users/1/posts/12432"
}
```

* 响应失败
  * 状态码
      + 401 UNAUTHORIZED
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Invalid email/phone or password",
  "api_url": "/api"
},
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)


#### POST `/api/posts/`

* 描述：增加一个帖子

* 请求
  
  * 请求体样例

``` json
{
  "name": "manley",
  "password": "123456",
  "content": "要认真学习，不然后果很惨",
  "label":"学习"
}
```

* 响应成功
  * 状态码
        + 201 CREATED
  * 响应体样例

``` json
{
  "url": "/api/posts/96612621"
}
```

* 响应失败
  * 状态码
      + 401 UNAUTHORIZED
      + 404 NOT FOUND
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Invalid email/phone or password",
  "api_url": "/api"
},
{
  "message": "Not found",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)

#### DELETE `/api/users/{userId}/`

* 描述：删除某个用户

* 请求
  * 请求体参数
      用户名，密码
  * 请求体样例

``` json
{
  "name":"manley",
  "password": "1123443sdf"
}
```

* 响应成功
  * 状态码
      + 204 NO CONTENT
  * 无响应体


* 响应失败
  * 状态码
      + 401 UNAUTHORIZED
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Invalid email/phone or password",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)

#### DELETE `/api/users/{userId}/posts/postId/`

* 描述：删除某个用户的某个帖子

* 请求
  * 请求体参数
      用户名，密码
  * 请求体样例

``` json
{
  "name":"manley",
  "password": "1123443sdf"
}
```

* 响应成功
  * 状态码
      + 204 NO CONTENT
  * 无响应体


* 响应失败
  * 状态码
      + 401 UNAUTHORIZED
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Invalid email/phone or password",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)


#### DELETE `/api/posts/{postId}/`

* 描述：删除某个帖子

* 请求
  * 请求体参数
      用户名，密码
  * 请求体样例

``` json
{
  "name":"manley",
  "password": "1123443sdf"
}
```

* 响应成功
  * 状态码
      + 204 NO CONTENT
  * 无响应体


* 响应失败
  * 状态码
      + 401 UNAUTHORIZED
      + 503 SERVICE UNAVAILABLE
  * 响应体

``` json
{
  "message": "Invalid email/phone or password",
  "api_url": "/api"
},
{
  "message": "Server is busy",
  "api_url": "/api"
}
```

[back to Content](#content)
