# Backend

## MANUAL SEND COOKIES

Inside the [person file controller](./src/controllers/person.js) you will find the changes to add to be able to send the token manually

```javascript
module.exports.registerPerson = async (req, res, next) => {
  // ...
  res
    .status(200)
    .cookie('auth_token', person_token[0], {
      sameSite: 'none',
      secure: true,
      expires: new Date(2147483647 * 1000),
    })
    .json({
      messsage: 'Person was registered successfully!',
      data: [
        {
          first_name: req.body.first_name,
          last_name: req.body.last_name,
          // ======================= SEND MANUAL COOCKIE =======================
          auth_token: person_token[0],
          // ===================================================================
        },
      ],
    });
};
```

```javascript
module.exports.loginPerson = async (req, res, next) => {
  // ...
  res
    .status(200)
    .cookie('auth_token', person_token[0], {
      sameSite: 'none',
      secure: true,
      expires: new Date(2147483647 * 1000),
    })
    .json({
      messsage: 'Person was registered successfully!',
      data: [
        {
          first_name: req.body.first_name,
          last_name: req.body.last_name,
          // ======================= SEND MANUAL COOCKIE =======================
          auth_token: person_token[0],
          // ===================================================================
        },
      ],
    });
};
```
