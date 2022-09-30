
# Why did I make this repo?

Simple. Just to inform some unique, easy to use, hidden gems library, tech, etc. That are rarely known or used by developers.




## json-server 
**Frontend Dev**

Fake REST API with zero coding in less than 30 seconds (seriously).
Created for front-end developers who need a quick back-end for prototyping and mocking.

- [Documentation](https://www.npmjs.com/package/json-server) 
- [Github](https://github.com/typicode/json-server)

Simple way to use it
- Create a folder in **/src** called **data**
- Then make a file **db.json** 
- Write DB in JSON format like this, (like mongoose?)
```
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```
- Then install the library
```
  npm install json-server
```
- After the library is installed, you can run the virtual server like this
  
  - --watch data/db.json -> the virtual DB is on file called **db.json** in **data** folder
  - --port 8000 -> run the server on http://localhost:8000/
```
  npm json-server --watch data/db.json --port 8000
```
- This virtual local server acts like real server (no cap 🧢)
```
import axios from "axios";

import { updateStart, updateSuccess, updateError } from "./userSlice";

export const updateUser = async (user, dispatch) => {
    dispatch(updateStart());
    try {
        const res = await axios.post("http://locallhost:8000/user", user);
        dispatch(updateSuccess(res.data));
    } catch (err) {
        console.log(err.toJSON())
        dispatch(updateError(err.toJSON().message));
    }
}
```

    
