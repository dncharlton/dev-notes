### GET
```js
async function getUserById(baseURL, id, apiKey) {
  const fullURL = `${baseURL}/${id}`
  const response = await fetch(fullURL, {
    method: 'GET',
    mode: 'cors',
    headers: {
      'X-API-Key': apiKey,
      'Content-Type': 'application/json'
    }
  })
  return response.json()
}
```


### PUT
```js
async function updateUser(baseURL, id, data, apiKey) {
  const fullURL = `${baseURL}/${id}`
  const response = await fetch(fullURL, {
    method: 'PUT',
    mode: 'cors',
    headers:{
      'X-API-Key': apiKey,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(data)
  })
  return response.status
}
```

`PUT` vs `PATCH` -> Put typically updates entire resources while patch updates a partial resource, despite this servers will typically prefer the `PUT` method.


### DELETE
```js
async function deleteUser(baseURL, id, apiKey) {
  const fullURL = `${baseURL}/${id}`
  const response = await fetch(fullURL, {
    method: 'DELETE',
    mode: 'cors',
    headers: {
      'X-API-Key': apiKey
    }
  })
  return response.status
}
```


