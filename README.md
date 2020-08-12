# Ejercicio-gesti-n-de-rutas
const express = require('express')
const app = express()
const port = 3000

let bodyParser = require('body-parser');
app.use(bodyParser.json());

let products = [];

app.route('/products')
 .get((req, res) => {
   res.json(products);
 })
 .post((req, res) => {
   const newProduct = { ...req.body, id: products.length + 1 }
   products = [...products, newProduct]
   res.json(newProduct);
 })
.put((req, res) => {
   let updatedProduct;
   products = products.map(p => {
     if (p.id === req.body.id) {
       updatedProduct = { ...p, ...req.body };
       return updatedProduct;
     }
     return p;
   })
   res.json(updatedProduct);
 })
 .delete((req, res) => {
   const deletedProduct = products.find(p => p.id === +req.body.id);
   products = products.filter(p => p.id !== +req.body.id);
   res.json(deletedProduct);
 })

app.listen(port, () => console.log(`Example app listening on port ${port}!`))




PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\no841:27)Received data []                                             modules/run_main.js:71:12)
Connection closed
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> node client-post.js
response {"name":"product","id":1}                           s/nodejs-http/exercise-express-routing/reading-writing
Closed connection                                            dejs-http\exercise-express-routing\reading-writing> node client-get.js
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> node client-get.js                                                    dejs-http\exercise-express-routing\reading-writing> node client-post.js
Received data [{"name":"product","id":1}]
Connection closed
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing>
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essenode client-post.jsexercise-express-routing\reading-writing>
response {"name":"product","id":1}
Closed connection
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> node client-put.js
response {"name":"product-updated","id":1}
Closed connection
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> node client-get.js
Received data [{"name":"product-updated","id":1}]
Connection closed
esponse {"name":"product","id":1}
Closed connection
response {"name":"product","id":1}
Closed connection
Received data []
Connection closed
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing>

                                                                                                                 node client-post.js
response {"name":"product","id":1}
Closed connection
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> node client-delete-route.js
response {"name":"product","id":1}
Closed connection
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> node client-get.js
Received data []
Connection closed
PS C:\Users\Edison\Desktop\ejercicio rutas\node-essentials\nodejs-http\exercise-express-routing\reading-writing> 


