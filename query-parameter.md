# Query Parameter 

import express from "express";
const app = express();
const port = 3000;

app.get("/search", (req, res) => {
    console.log(req.query);  // Logs the query params as an object
    res.send(`You searched for ${req.query.query}, Page: ${req.query.page}`);
});

app.listen(port, () => {
    console.log(`Server running on port ${port}`);
});
