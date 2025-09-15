- # global datatype
```js
import { Connection } from "mongoose"

  

declare global {

var mongoose: {

conn: Connection | null

promise: Promise<Connection> | null

}

}

  

export {}

```

- # db connection
```js
import mongoose from "mongoose";

const MONGODB_URL = process.env.MONGODB_URL!;

  

if (!MONGODB_URL) {

throw new Error("Please define mongodb url in env file");

}

  

let cached = global.mongoose;

  

if (!cached) {

cached = global.mongoose = { conn: null, promise: null }

}

  

export async function connectionToDatabase() {

if (cached.conn) {

return cached.conn;

}

  

if (!cached.promise) {

const opts = {

bufferCommands: true,

maxPoolSize: 10

}

  

cached.promise = mongoose.connect(MONGODB_URL, opts)

.then(() => mongoose.connection);

}

  

try{

cached.conn = await cached.promise;

}catch(error){

cached.promise = null;

throw error;

}

  

return cached.conn;

}
```
