# type anything after files/, it'll take you to the same exact location

import express from "express";
const app = express();
const port = 3000;

app.listen(port, ()=>{
    console.log(`Server is running on port: ${(port)}`)
});

app.get("/files/:fileName", (req,res)=>{
    const name = req.params.fileName;
    console.log(name);
    res.json({});
});
