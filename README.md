# node.js-
创建服务器模板

原生HTTP版

const http = require("http")
const fs = require("fs")
const path = require("path")

const server = http.createServer()

server.on("request", (req,res) => {
    //获取请求的url信息
   let url = req.url
    // 如果是根目录请求，返回首页
    if(url == "/") url = "/index.html"

    fs.readFile(path.join(__dirname, "/views" + url), function(err,buf){
        if(err) return res.end("404 not defind")

        res.end(buf)
    })
})

server.listen("8080", "127.0.0.1", function(){
    console.log("启动成功，地址为http://127.0.0.1");
    
})


// 
