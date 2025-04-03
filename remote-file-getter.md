# remote file getter

import express from "express";
import fs from "fs";
const app = express();
const port = 3000;

app.listen(port, ()=>{
    console.log(`Server is running on port: ${(port)}`)
});

app.get("/files/:fileName", (req,res)=>{
    const name = req.params.fileName;
    console.log(name);
    fs.readFile(name,"utf-8",(err,data)=>{
        res.json({
            data
        });
    });
    
});
