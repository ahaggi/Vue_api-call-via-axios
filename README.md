
# Axios
Using Axios to Consume APIs which is an altirnative of using Fetch-js.

https://github.com/axios/axios

**Install**
npm install axios

**Usage**

Requests can be made by passing the relevant config to axios.

```js
let config = {
    method: "post",
    url: "http://127.0.0.1:5002/login",
};
let response = await axios(config);
```

Or using request method aliases


axios.request(config)  
axios.get(url[, config])  
axios.delete(url[, config])  
axios.head(url[, config])  
axios.options(url[, config])  
axios.post(url[, data[, config]])  
axios.put(url[, data[, config]])  
axios.patch(url[, data[, config]])  


**Example**
```js
      try {
        let config ={
          method: "post",
          url: "http://127.0.0.1:5002/login",
          data: {
            password: "password1",
            username: "user1",
          },
          withCredentials: true,
        };

        let response = await axios(config);
        console.log(response.data);
      } catch (err) {
        console.log(err);
      } finally {
        loading.value = false;
      }

      try {
        let response = await axios.get("http://127.0.0.1:5002/users", {
          withCredentials: true,
        });
        dataList.value = response.data;
        console.log(dataList.value);
      } catch (err) {
        console.log(err);
      } finally {
        loading.value = false;
      }

      try {
        let response = await axios.get("http://127.0.0.1:5002/logout", {
          withCredentials: true,
        });
        console.log(response.data);
      } catch (err) {
        console.log(err);
      } finally {
        loading.value = false;
      }

      try {
        let response = await axios.get("http://127.0.0.1:5002/users", {
          withCredentials: true,
        });
        dataList.value = response.data;
        console.log(dataList.value);
      } catch (err) {
        console.log(err);
      } finally {
        loading.value = false;
      }
    };
```