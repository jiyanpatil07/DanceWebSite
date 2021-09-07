const express = require("express");
const path = require("path");
const bodyparser = require("body-parser");
const app = express();
const port = 3000;

// mongoose
const mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/contactDance', {useNewUrlParser: true, useUnifiedTopology: true});

//  Define Mongoose Schema
const ContactSchema = new mongoose.Schema({
    name: String,
    age: String,
    phno: String,
    email: String,
    desc: String
  });

  const Contact = mongoose.model('Contact', ContactSchema);


// EXPRESS STUFF
app.use('/static',express.static('static'));// For serving static files
app.use(express.urlencoded());

// PUG STUFF
app.set('view engine','pug');// Set the template engine as pug
app.set('views',path.join(__dirname,'views'));// Set the views directory

// END POINTS
app.get('/',(req,res)=>{
   
    const params = {};
    res.status(200).render('home.pug',params);
});
app.get('/contact',(req,res)=>{
   
    const params = {};
    res.status(200).render('contact.pug',params);
});
app.post('/contact',(req,res)=>{
    var myData = new Contact(req.body);
    myData.save().then(()=>{
        res.send("This item is saved to database")
    }).catch(()=>{
        res.status(400).send("Item not saved!");
    })
   
    // res.status(200).render('contact.pug');
});


// start server
app.listen(port,()=>{
    console.log(`Application started successsfully on Port:${port}`);
});
