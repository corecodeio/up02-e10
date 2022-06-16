# Frontend

## MANUAL SET COOKIES

Inside the [auth provider file](./src/context/AuthProvider.js) you will find the changes to add to be able to set the token manually

```javascript
// ======================= USE OF SET COOKIE =======================
const [cookies, setCookie, removeCookie] = useCookies(['auth_token']);
// ==================================================================
```

```javascript
const register = (first_name, last_name, email, password) => {
  // ...
  const data = await response.json();
  // ======================= SET MANUAL COOCKIE =======================
  setCookie('auth_token', data.data[0].auth_token, {
    expires: new Date(2147483647 * 1000),
  });
  // ==================================================================
  setCurrentUser(data.data[0]);
  resolve();
  // ...
};
```

```javascript
const login = (email, password) => {
  // ...
  const data = await response.json();
  // ======================= SET MANUAL COOCKIE =======================
  setCookie('auth_token', data.data[0].auth_token, {
  expires: new Date(2147483647 * 1000),
  });
  // ==================================================================
  setCurrentUser(data.data[0]);
  resolve();
  // ...
};
```

```javascript
useEffect(() => {
  const getUserInfo = async () => {
    // ...
    const data = await response.json();
    // ======================= SET MANUAL COOCKIE =======================
    data.data[0].auth_token = cookies.auth_token;
    // ==================================================================
    setCurrentUser(data.data[0]);
    // ...
  };
  // ...
}, []);
```
