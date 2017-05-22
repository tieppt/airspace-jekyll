---
id: 58
title: Nodejs Babel use ES2015 in Server Side
date: 2016-09-24T05:16:30+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=58
permalink: /nodejs-babel-use-es2015-server-side/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2016/09/nodejs-es2015.png
categories:
  - Lập Trình
  - Programming
tags:
  - Babel
  - ES2015
  - Nodejs
---
<h2 style="text-align: center;">
  Nodejs Babel use ES2015 in Server Side
</h2>

In this article we&#8217;ll build a simple Nodejs project use ES2015 in server side, using Babel Require Hook to make on-the-fly transpilation.

<!--more-->

First, create _package.json_ file then paste following code:

<pre class="theme:vs2012-black toolbar:1 lang:js decode:true">{
  "name": "es2015-nodejs-babel-require-hook",
  "version": "1.0.0",
  "description": "A Nodejs Project using ES2015 with Babel Require Hook",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "keywords": [
    "ES2015",
    "ES6",
    "nodejs"
  ],
  "author": "Tiep Phan",
  "license": "ISC",
  "dependencies": {
    "babel-register": "^6.14.0",
    "express": "^4.14.0"
  },
  "devDependencies": {
    "babel-preset-es2015": "^6.14.0"
  }
}
</pre>

This file decide what library we need include: babel, express. And a script to start project.

After that, we create configuration file for Babel:

_.babelrc_

<pre class="theme:vs2012-black toolbar:1 lang:js decode:true">{
  "presets": ["es2015"]
}</pre>

Then we create _index.js_

<pre class="theme:vs2012-black toolbar:1 lang:js decode:true">require("babel-register");
require('./server');</pre>

And _server.js_

<pre class="theme:vs2012-black toolbar:1 lang:js decode:true">import express from 'express';
import {users} from './models/Users';

let app = express();

app.get('/', (req, res) =&gt; {
  res.send('Hello World!');
});

app.get('/api/users', (req, res) =&gt; {
    res.json(users);
});

app.listen(3300, () =&gt; {
  console.log('Example app listening on port 3300!');
});</pre>

Create a _models_ directory then create _Users.js_ file, after that we&#8217;ll put following code:

<pre class="theme:vs2012-black toolbar:1 lang:js decode:true ">export let users = [
    {
        'name': 'Tiep Phan',
        'job': 'Web Developer'
    }, {
        'name': 'John L',
        'job': 'Software Architect'
    }
];</pre>

That&#8217;s it.

Run _npm install _to download all dependencies. Then run _npm start_ to see result.

If you using _Nodemon, _you can run _nodemon index.js._

We defined 2 routes: root (/) and users api (/api/users) you can test on browser like this:

<a href="http://localhost:3300" target="_blank">http://localhost:3300</a>

or:

<a href="http://localhost:3300/api/users" target="_blank">http://localhost:3300/api/users</a>

&nbsp;

Source code in Github: <https://github.com/tieppt/es2015-nodejs-babel-require-hook>

Happy coding!

&nbsp;

&nbsp;