---
layout: post
title:      "Bootstrap Fundamentals"
date:       2019-10-13 22:12:16 -0400
permalink:  bootstrap_fundamentals
---


I'm going to walk through some fundamental steps of setting up and using bootstrap with my React app to achieve a more modern look.

[This resource](https://blog.logrocket.com/how-to-use-bootstrap-with-react-a354715d1121/) was especially helpful in walking me through different ways I could implement Bootstrap.  For my application, I chose to implement Bootstrap via option 2 - 'Bootstrap as a Dependency'.  This ended up being very simple to implement.

**Setting It Up**

First, I ran `npm install bootstrap` in my terminal to install the bootstrap dependency for my app.

Second, I ran `npm install jquery popper.js` in my terminal to install the jquery and popper.js dependencies for my app.  These are both needed to make Bootstrap javascript functionality work.

Lastly, I included the following lines in my src/index.js file.
```
import 'bootstrap/dist/css/bootstrap.min.css';
import $ from 'jquery';
import Popper from 'popper.js';
import 'bootstrap/dist/js/bootstrap.bundle.min';
```

These three steps download and import the Bootstrap javascript and css capabilities into the heart of my React app, and I am ready to get bootstrapping!

**Using It**

I'd like to set up a drop down menu bar for my site navigation.  Looking to Bootstraps documentation, I can easily read how to accomplish this.  This is what my navigation looked like before (simply two links at the bottom of my page):

```
<Link to='/login'>Log In</Link>
<Link to='/find'>Find Wedding</Link>
```

In order to turn this into a button with dropdown capability, I implement the following:

```
<div class="dropdown">
    <a class="btn btn-secondary dropdown-toggle" href="#" role="button" id="dropdownMenuLink" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
        <i class="fas fa-bars"></i>
    </a>

    <div class="dropdown-menu" aria-labelledby="dropdownMenuLink">
        <Link class="dropdown-item" to='/login'>Login</Link>
        <Link class="dropdown-item" to='/find'>Find Wedding</Link>
    </div>
</div>
```

By enclosing my Link tags within a "dropdown-menu" div, adding a button with a class "btn btn-secondary dropdown-toggle", and enclosing this code all within a class of "dropdown", I utilize Bootstrap's pre-set js and css to create a dropdown button.

Please note above that popper.js is required for this to work.  I also utilized font-awesome to display the bars icon for my dropdown button.

And that's it!  I now have an interactive, modern looking button to control my navigation.

