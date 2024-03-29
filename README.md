# My Little Trick.

## Why did I make this repo?
Simple. Just to save snippet code, library, VSCode extension that I use on daily basis and that are rarely known or used by developers.

#### **List of contents**

<details>
<summary><b>json-server</b></summary>

### json-server  

**Frontend Dev Node Library**

Fake REST API with zero coding in less than 30 seconds (seriously).
Created for front-end developers who need a quick back-end for prototyping and mocking.

- [Documentation](https://www.npmjs.com/package/json-server) 
- [Github](https://github.com/typicode/json-server)

Simple way to use it
- Create a folder in **/src** called **data**
- Then make a file **db.json** 
- Write DB in JSON format like this, (like MongoDB?)
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
- This virtual local server acts like real server
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
</details>

<details>
<summary><b>Window Dimension</b></summary>

### Window Dimension 
**Frontend Dev Code**

It's not a library, but a piece of code (made up hook) to get the height and width of browser window.

- Put this code as a hook, util, or other like `useWindowDimensions.js`.
```
import { useEffect, useState } from "react";

function getWindowDimensions() {
  const { innerWidth: width, innerHeight: height } = window;
  return {
    width,
    height
  };
}

export default function useWindowDimensions() {
  const [windowDimensions, setWindowDimensions] = useState(
    getWindowDimensions()
  );

  useEffect(() => {
    function handleResize() {
      setWindowDimensions(getWindowDimensions());
    }

    window.addEventListener("resize", handleResize);
    return () => window.removeEventListener("resize", handleResize);
  }, []);

  return windowDimensions;
}
```

- It will be returned as an object. Then import and destructure it in other file 
```
import useWindowDimensions from './hooks/useWindowDimensions';

const { width, height } = useWindowDimensions();

```
</details>


<details>
<summary><b>Polacode 📸</b></summary>

### Polacode 📸
**Visual Studio Code Extension**

Polacode 📸 is a VSCode extension to easily capture your code! Instead of using [carbon.now.ssh](https://carbon.now.sh/) to take a beautiful capture of your code, you can use Polacode in a faster way. 
- [VSCode Marketplace](https://marketplace.visualstudio.com/items?itemName=pnp.polacode)


Simple way to use it
- Install the **Polacode** 📸 Extension first 
- Press `ctrl + shift + p`
- Search for `Polacode 📸` and press `enter`
- Block some code and copy it with `ctrl + c`
- Paste it on Polacode 📸 tab with `ctrl + v`
- You're good with it!

![alt text](https://media.discordapp.net/attachments/1021751620331126865/1031106322323734548/code_example.png?width=778&height=415)

</details>

<details>
<summary><b>ts-node-dev</b></summary>

## ts-node-dev
**Backend Dev Node Library**

It restarts target node process when any of required files changes (as standard node-dev) but shares Typescript compilation process between restarts. This significantly increases speed of restarting server because there is no need to instantiate `ts-node` compilation each time; 

`TLDR : Nodemon but for ts`
- [Documentation](https://www.npmjs.com/package/ts-node-dev) 
- [Github](https://github.com/wclr/ts-node-dev)

Simple way to use it
- `npm i ts-node-dev --save-dev` | `yarn add ts-node-dev --dev`
- Usage : `ts-node-dev [node-dev|ts-node flags] [ts-node-dev flags] [node cli flags] [--] [script] [script arguments]`
- Example : `ts-node-dev --respawn --transpile-only --exit-child --watch src index.ts`

</details>

<details>
<summary><b>Markdown Preview</b></summary>

### Markdown Preview 
**Visual Studio Code Extension**

Markdown Preview lets you compile markdown like README.md and others on your VS Code Text Editor. It will automatically run and compile as you make changes in your markdown file.

- [VSCode Marketplace](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)
- [Github](https://github.com/shd101wyy/vscode-markdown-preview-enhanced)

Simple way to use it
- Install the **Markdown Preview Enhanced** Extension first 
- Press `ctrl + k + v` for quick shortcut
- You're good with it!

</details>