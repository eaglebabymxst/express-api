Cách thiết lập Server Express API trong Node.js
Cài đặt
    Kiểm Tra Phiên Bản:
        node -v
        npm -v
    Tạo File:
        mkdir express-api 
    Chuyển đến File
        cd express-api
Khởi Tạo Dự Án:
    npm init
    "name": "express-api",
    "version": "1.0.0",
    "description": "Node.js and Express REST API",
    "main": "index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
    "author": "Tania Rascia",
    "license": "MIT"
Install body-parser: Middleware dùng để phân tích body
    npm install body-parser express mysql request
        "name": "express-api",
        "version": "1.0.0",
        "description": "Node.js and Express REST API",
        "main": "index.js",
        "test": "echo \"Error: no test specified\" && exit 1"
        "author": "Tania Rascia",
        "license": "MIT",
        "dependencies": {
        "dependencies": {
            "body-parser": "^1.18.3",
            "express": "^4.16.3",
            "mysql": "^2.16.0",
            "request": "^2.88.0"
            }
            }
Thiết lập http server:
    const http = require('http');
    const port = 3001;
    const server = http.createServer();
    server.on('request',(request, response) => {
        console.log(`URL: ${request.url}`);
        response.end('Hello, server!')
    })
    server.listen(port, (error) => {
        if (error) return console.log(`Error: ${error}`);
        console.log(`Server is listening on port ${port}`)
    })
Run Server:
    node hello-server.js
Kết quả:
    
//
Thiết lập một Express Server
    Tạo 1 File js tên là app.js:
        const express = require('express');
        const port = 3002;
        const app = express();
        app.get('/', (request, response) => {
            console.log(`URL: ${request.url}`);
            response.send('Hello, Server!');
        });
        const server = app.listen(port, (error) => {
            if (error) return console.log(`Error: ${error}`);
        
            console.log(`Server listening on port ${server.address().port}`);
        })
Định tuyến:
    Tạo 1 thư mục routes và 1 file routes.js trong nó
        const router = app => {
            app.get('/', (request, response) => {
                response.send({
                    message: 'Node.js and Express REST API'
                });
            });
        }   
    Exports nó ra ngoài:
        module.exports = router;
    Trong app.js:
        Khai báo:
            const routes = require('./routes/routes');
    Run: 
        node app.js
    Tạo 1 Json:
        const users = [{
        id: 1,
        name: "Richard Hendricks",
        email: "richard@piedpiper.com",
            },
            {
                id: 2,
                name: "Bertram Gilfoyle",
                email: "gilfoyle@piedpiper.com",
            },
        ];
    Đổi biến router vừa khai báo ở trên thành:
        const router = app => {
            app.get('/', (request, response) => {
                response.send(users);
            });
        }
    Run:
        node app.js
    Kết quả
        ![image](https://user-images.githubusercontent.com/46476419/176987783-44bd9f39-0d06-4afd-a7a1-889cb63d793d.png)
