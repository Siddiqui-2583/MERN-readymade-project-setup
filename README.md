# MERN-readymade-project-setup
This is a readymade MERN stack project setup.
Steps followed to make this project setup:

1. Create a folder with your project name.

2. Create a folder named client or frontend inside project folder
3. cd client
   npx create-react-app ./
   npm install axios @material-ui/core react-router-dom moment react-file-base64 redux redux-thunk
4. In package.json of client add "proxy": "http://localhost:5000", before dependencies scope
5. Package.json of client: 
```

{
  "name": "frontend",
  "version": "0.1.0",
  "private": true,
  "proxy": "http://localhost:5000",
  "dependencies": {
    "@testing-library/jest-dom": "^5.11.9",
    "@testing-library/react": "^11.2.3",
    "@testing-library/user-event": "^12.6.2",
    "react": "^17.0.1",
    "react-dom": "^17.0.1",
    "react-scripts": "4.0.1",
    "web-vitals": "^0.2.4"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}

```

6. Create a folder named server or backend inside project folder
7. create index.js file inside server folder 
8. Paste the below code in index.js-

import express from "express";
import bodyParser from "body-parser";
import mongoose from "mongoose";
import cors from "cors";
 
import bookRoutes from "./routes/bookRoutes.js";
const app = express();
 
app.use("/books", bookRoutes);
 
app.use(bodyParser.json({ limit: "30mb", extended: true }));
app.use(bodyParser.urlencoded({ limit: "30mb", extended: true }));
app.use(cors());

const CONNECTION_URL =
  "mongodb+srv://dbUser:<password>@cluster0.evhow.mongodb.net/<dbname>?retryWrites=true&w=majority";
 
app.get("/", (req, res) => {
  res.send("Hlw Shourav");
});
 
const PORT = process.env.PORT || 5000;
 
mongoose
  .connect(CONNECTION_URL, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() =>
    app.listen(PORT, () => console.log(`Server is running at port ${PORT}'`))
  )
  .catch((e) => console.log(e.message));
mongoose.set("useFindAndModify", false);
 

9. cd server
   npm init -y
   npm install body-parser cors express mongoose nodemon
10. In package.json of server add "type":"module", before script scope
11. Package.json of server:
```

	{
  "name": "backend",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "start": "nodemon index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "body-parser": "^1.19.0",
    "cors": "^2.8.5",
    "express": "^4.17.1",
    "mongoose": "^5.11.13",
    "nodemon": "^2.0.7"
  }
}
 
 ```


