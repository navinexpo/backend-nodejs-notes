# Why do we use body-parser

- Its a `middleware` that processes the `body` of an incoming *HTTP request*.
- When a client sends a request to the server. This data could be in various formats: `JSON`, `URL-encoded form data`, or `raw data`. 
- The **body-parser** extracts this data and makes it avaiable to the server through the `req-body`.

`Types of body-parser`
- Parse incoming requests with JSON payloads.
- This middleware is built into Express and can be used directly. 

1. `express.json()`:
```
import express from 'express';

const app = express();

app.use(express.json())
app.post('/data', (req, res)=> {
    console.log(req.body); //Access the parsed JSON Data.
    res.send('Data received')
});
app.listen(3000, ()=> console.log('Server runnig on the port 3000'));
```
2. `express.urnlencoded()`:
- Parses incoming requests with URL-encoded payloads (typically from HTML forms).
- It uses the `querystring` library for parsing.
```
import express from 'express'

const app = express();

app.use(express.urlencoded({ extended: true }));

app.post('/data', (req, res)=> {
    console.log(req.body); //access the parsed form data. 
    res.send('Form data received');
});
app.listen(3000, ()=> console.log('Server running on port 3000));
```
3. `body-parser` (legacy middleware):
- Before Express 4.16.0 `body-parser` was commonly used as a standalone middleware to handle different data formats. 
- It has now been integrated into Express.

```
import express from 'express';
import body-parser from 'body-parser'

const app = express();

app.use(bodyParser.json());
app.use(bodyParser.urlEncoded({ extended: true }));

app.post('/data', (req, res)=> {
    console.log(req.body) //access the parsed data
});
app.listen(3000, ()=> console.log('Server running on port 3000'));
```

**Key-Concept**
- `JSON Parsing`: 


