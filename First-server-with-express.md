# learning-express
just created my first server with express

### used GET to avoid the cannot GET
import express from "express";
const app = express();
const port = 3000;

app.get("/", (req, res)=>{
    // console.log(req.rawHeaders)
    res.send("<h1>A new begining</h1>");
});

app.get("/message", (req, res)=>{
    res.send("<h3> Message </h3> <p>Mern stack I'm coming for you</p>")
});

app.get("/contact", (req, res)=>{
    res.send("<h3>Contact me </h3> <p>nitish.ksharmaa@gmail.com</p>")
});

app.listen(port, ()=>{
    console.log(`server running on port ${port}`);
});
