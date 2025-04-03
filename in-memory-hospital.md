// an in memory hospital
// you need to create 4 routes (4 things that the hospital can do)
// 1- GET - User can check how many kidneys they have and their health
// 2- POST - User can add a new kidney
// 3- PUT - User can replace a kidney and make it healthy
// 4- Delete - User can remove a kindey

import express from "express";
const app = express();
const port = 3000;

app.use(express.json());

const users = [{
    name: "Pewcalypse",
    kidneys: [{
        healthy:false 
    }]
}];

app.listen(port, ()=>{
    console.log(`Server runnning on port ${(port)}`)
});

app.get("/", (req,res)=>{
    const pewcalypseKidneys = users[0].kidneys;
    const numberOfKidneys = pewcalypseKidneys.length;
    let numberOfHealthyKidneys = 0;
    for(let i=0; i<pewcalypseKidneys.length; i++){
        if (pewcalypseKidneys[i].healthy){
            numberOfHealthyKidneys = numberOfHealthyKidneys +1;
        }
    }
    const numberOfUnhealthyKidneys = numberOfKidneys - numberOfHealthyKidneys;
    res.json({
        numberOfKidneys,
        numberOfHealthyKidneys,
        numberOfUnhealthyKidneys
    });
});

app.post("/", (req,res)=>{
    const isHealthy = req.body.isHealthy;
    users[0].kidneys.push({
        healthy:isHealthy
    });
    res.json({
        msg: "Done!"
    });
});

app.put("/", (req,res)=>{
    for (let i=0; i<users[0].kidneys.length; i++){
        users[0].kidneys[i].healthy = true;
    }
    res.json({});
})

app.delete("/", (req,res)=>{
    const newKidneys = [];
    let atleastOneUnhealthyKidney = false;
    for (let i=0; i<users[0].kidneys.length; i++){
        if (users[0].kidneys[i].healthy){
            newKidneys.push({
                healthy: true
            })
        }
    }
    users[0].kidneys = newKidneys;
    res.json({msg: "deleted"});
})
