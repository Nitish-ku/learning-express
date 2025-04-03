## Sum of First N Numbers using Express.js

import express from "express";
const app = express();
const port = 3000;

function sum(n){
    let ans = 0;
    for(let i = 1; i<=n; i++){
        ans = ans+i;
    }
    return ans;
}

app.listen(port, ()=>{
    console.log(`Server runnning on port ${(port)}`)
});

app.get("/", (req,res)=>{
    const n = req.query.n;
    const ans = sum(n);
    res.send("Hi your answer is : " + ans);
})
