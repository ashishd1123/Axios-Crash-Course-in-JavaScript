# Axios-Crash-Course-in-JavaScript
In this video we are looking how to operates Axios HTTP client to make requests in JavaScript, and it is a promise-based HTTP library that allows developers to make HTTP requests to their own servers or third sources.  These requests are made in several different ways.

## How to install Axios

Install Axios using **Node Package Manager**
```bash
$ mkdir axios-js-example
$ cd axios-js-example
$ npm init -y
$ npm install axios
```

Install Axios using **jsDelivr CDN**
```bash
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```

Install Axios using **unpkg CDN**
```bash
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

## Getting Started with Axios
In this section, we will learn how to send various HTTP requests using Axios in Node.js. We will be making REST API calls to an e-commerce back-end application for the following operations:
```bash
  • GET - To get all the products in one category, eg: all mobiles
  • POST - To create a new product in the database
  • PUT - To modify an existing product data
  • DELETE - To delete an existing product
```

## Make HTTP Requests - GET Request

```bash
axios.get('endpoit url')
  .then(function (response) {
       console.log(response);
       console.log(response.data);
	})
	  .catch(function (error) {
	      console.log(error);
	});
```

**OR**

```bash
axios({
    method: 'get',
    url: 'endpoint url', 
    responseType: 'json'
})
  .then(function (response) {
       console.log(response);
})
  .catch(function (error) {
      console.log(error);
})
```

## Make HTTP Requests - POST Request

```bash
function userId() {
    return ([17]+13).replace(/[0-9]/g, c =>
      (c ^ crypto.getRandomValues(new Uint8Array(1)))
    );
}
```

```bash
var obj = {
    id        : userId(),
    name      : 'Mad Tech 2', 
    email     : 'madtech2@gmail.com', 
    position  : 'developer', 
    phone     : 334543545,
    gender    : 'male',
    confirmation   : false
}
```

```bash
axios.post('http://localhost:8080/api/users', obj)
.then(function (response) {
    console.log(response.data);
})
.catch(function (error) {
    console.log(error);
});
```

**OR**

```bash
axios({
    method: 'post',
    url: 'http://localhost:8080/api/users', 
    data: obj
})
  .then(function (response) {
       console.log(response);
  })
  .catch(function (error) {
      console.log(error);
});
```

## Make HTTP Requests - DELETE Request

```bash
axios.delete('http://localhost:8080/api/users/818581240')
  .then(function (response) {
       console.log(response);
  })
  .catch(function (error) {
      console.log(error);
  });
```

**OR**

```bash
axios({
    method: 'delete',
    url: 'http://localhost:8080/api/users/10420212777', 
    data: obj
})
  .then(function (response) {
       console.log(response);
  })
  .catch(function (error) {
      console.log(error);
});
```

## Make HTTP Requests - PUT Request

```bash
var updateObj = {
    id        : "24823610200",
    name      : 'Mad Tech', 
    email     : 'madtech3@gmail.com', 
    position  : "Senior Software Engineer", 
    phone     : "335345343",
    gender    : 'Male',
    confirmation   : false
}
```

```bash
axios({
    method: 'patch',
    url: 'http://localhost:8080/api/users/24823610200', 
    data: updateObj
})
.then(function (response) {
    console.log(response);
})
.catch(function (error) {
    console.log(error);
});
```

**OR**

```bash
axios({
    method: 'delete',
    url: 'http://localhost:8080/api/users/10420212777', 
    data: obj
})
  .then(function (response) {
       console.log(response);
  })
  .catch(function (error) {
      console.log(error);
});
```

## Performing multiple Concurrent requests
```bash
function getAllData() { 
    return axios.get('http://localhost:8080/api/users'); 
}
```

```bash
function getSingleData() { 
    return axios.get('http://localhost:8080/api/users/1615337137'); 
}
```

```bash
async function getData() {
    const [userDetail, usersDetails] = await Promise.all([getSingleData(), getAllData()]); 
    console.log('User Details------ ', userDetail, usersDetails)
}
```

```bash
getData();
```

**OR**

```bash
Promise.all([getSingleData(), getAllData()])
   .then(function ([userDetail, usersDetails]) {
     console.log('data----------- ', userDetail, usersDetails);
});
```

## Axios Error Handling with Async-Await
```bash
const getUser = async () => {
    try {
        const response = await axios.get('http://localhost:8080/api/users/vi/1615337137')
        // console.log(response);
    } catch ( err ) {
        console.log(err.response);
         if(err.response) {
              console.log(err.response.status);
              console.log(err.response.statusText);
              console.log(err.response.data);
         }
     }
  }
```

```bash
getUser();
```
