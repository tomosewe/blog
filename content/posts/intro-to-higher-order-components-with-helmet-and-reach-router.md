---
title: "Intro to Higher Order Components With Helmet and Reach Router"
date: 2018-09-03T14:50:28+12:00
draft: false
---

What are Higher Order Components? I've been trying to learn about HOCs for a while now and I've come up with a simple example that helps me understand it and hopefully can help others too.

The [React docs have a pretty decent explanation](https://reactjs.org/docs/higher-order-components.html), but I wanted to come up with a simpler example. Let's say we have an app that has multiple pages and we want the title to update based on what page we're on.

---

First let's setup a new react app using [create-react-app](https://github.com/facebook/create-react-app).

```bash
npx create-react-app hoc-reach-helmet-demo
```

Next, navigate to your new directory and let's install [Reach Router](https://reach.tech/router).

```bash
npm install @reach/router
```

We'll just be setting up a pretty basic app for this demo.

Create the following files.

`App.js`

```javascript
import { Link, Router } from "@reach/router";
import React from "react";
import { Dashboard } from "./Dashboard";
import { Home } from "./Home";

export default class App extends React.Component {
  render() {
    return (
      <div>
        <nav>
          <Link to="/">Home</Link> <Link to="dashboard">Dashboard</Link>
        </nav>
        <Router>
          <Home path="/" />
          <Dashboard path="dashboard" />
        </Router>
      </div>
    );
  }
}
```

`Home.js`

```javascript
import React from "react";

export class Home extends React.Component {
  render() {
    return (
      <div>
        <h2>Home page</h2>
      </div>
    );
  }
}
```

`Dashboard.js`

```javascript
import React from "react";

export class Dashboard extends React.Component {
  render() {
    return (
      <div>
        <h2>Dashboard</h2>
      </div>
    );
  }
}
```

We've got a nav that links to 2 separate pages. We want each of these pages to have different titles so to do that we're going to install [React Helmet](https://github.com/nfl/react-helmet).

```bash
npm install --save react-helmet
```

React Helmet is pretty easy to use. To change the title just add a `<Helmet>` component at the top of the render method.

Make the following changes to the render method for Home.js and Dashboard.js

`Home.js`

```javascript
import React from "react";
import { Helmet } from "react-helmet";

export default class Home extends React.Component {
  render() {
    return (
      <div>
        <Helmet>
          <title>Home page</title>
        </Helmet>
        <h2>Home page</h2>
      </div>
    );
  }
}
```

`Dashboard.js`

```javascript
import React from "react";
import { Helmet } from "react-helmet";

export default class Dashboard extends React.Component {
  render() {
    return (
      <div>
        <Helmet>
          <title>Dashboard</title>
        </Helmet>
        <h2>Dashboard</h2>
      </div>
    );
  }
}
```

This is great but I promised we'd be using Higher Order Components so let's use a HOC to change the title of any component that is passed in.

`withTitle.js`

```javascript
import * as React from "react";
import { Helmet } from "react-helmet";

function withTitle(WrappedComponent, title) {
  return class extends React.Component {
    render() {
      return (
        <div>
          <Helmet>
            <title>{title}</title>
          </Helmet>
          <WrappedComponent {...this.props} />
        </div>
      );
    }
  };
}

export default withTitle;
```

We can now use the HOC in Home.js and Dashboard.js

`Home.js`

```javascript
import React from "react";
import withTitle from "./withTitle";

class Home extends React.Component {
  render() {
    return (
      <div>
        <h2>Home page</h2>
      </div>
    );
  }
}

export default withTitle(Home, "Home page");
```

`Dashboard.js`

```javascript
import React from "react";
import withTitle from "./withTitle";

class Dashboard extends React.Component {
  render() {
    return (
      <div>
        <h2>Dashboard</h2>
      </div>
    );
  }
}

export default withTitle(Dashboard, "Dashboard");
```

Tidy up your imports on `App.js` and you're done!

```javascript
import { Link, Router } from "@reach/router";
import React from "react";
import Dashboard from "./Dashboard";
import Home from "./Home";

export default class App extends React.Component {
  render() {
    return (
      <div>
        <nav>
          <Link to="/">Home</Link>
          <Link to="dashboard">Dashboard</Link>
        </nav>
        <Router>
          <Home path="/" />
          <Dashboard path="dashboard" />
        </Router>
      </div>
    );
  }
}
```

Run the app to see the title change in the browser tab.

```bash
npm run start
```

![Title change in action!](/images/gifs/TitleChange.gif)

🔥🔥🔥 Celebrate! 🔥🔥🔥

All code for this demo can be found in this [GitHub repo](https://github.com/tomosewe/hoc-reach-helmet-demo).
