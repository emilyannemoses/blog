---
layout: post
title:  "OAuth with React"
---

Google's Client Side JavaScript OAuth 2.0 with ReactJS

This is a template and tutorial on how to integrate [Google's JavaScript Client Side OAuth 2.0][oauth] with [ReactJS][react] user login flow.

## Pre-requisites

1. Know Basic ReactJS. At least complete [this tutorial](https://reactjs.org/tutorial/tutorial.html).

1. Created a demo app with [Create React App](https://github.com/facebook/create-react-app).

    * **Note: We will not be building this app with `npm run build`**
<br><br>
1. You have a public GitHub account and/or other valid public domain (if you wish to host this web app demo in production)

1. You must have a [Google Devleoper](https://console.developers.google.com) account and be somewhat familiar with navigating the UI including:

    * Creating a new project

    * [Verifying properties](https://www.google.com/webmasters/verification/home)
    
        * `https://{username}.github.io` (or whatever URL you want to use) must be verified in this list.

        * Purchasing a doman directly through [Google Domains](https://domains.google) will automatically add it to your verified domains list.

    * Obtaining API keys and creating key restrictions

    * Obtaining a Client ID for a Web Application
    
      * Authorized origins should list both `http://localhost:3000` and `http://{username}.github.io`
      <br><br>
1. Basic CSS knowledge. You're on your own with creating CSS for your app.

## Pre-notes

1. You will not be able to submit this app for verification for OAuth. This means when the OAuth window pops up for the user, it will always alert the user that this is not a verified app. This is because it is a demo app and Google does not verify demos. Here's my official privacy statement: [privacy](https://emilyannemoses.github.io/privacy)

    * To experience the authentication flow, go to [https://emilyannemoses.github.io/oauth-react-demo](https://emilyannemoses.github.io/oauth-react-demo) and do the following:

    <img src="{{site.baseurl}}/images/userauthflow.gif">

2. After completing this tutorial, if you'd like to host it via a live website (if you've verified `https://{username}.github.io` URL with Google) you can follow these steps to [launch a `create-react-app` to GitHub Pages](https://github.com/gitname/react-gh-pages).

## This is what you'll be building

<img src="{{site.baseurl}}/images/oauthflow.gif">

### Table of contents

* [`App.js`](#app-component)

    * [Lines 1-13](#1-13)

    * [Lines 14-22](#14-22)

    * [Lines 87-89](#87-89)

    * [Lines 53-55](#53-55)

    * [Lines 56-86](#56-86)

    * [Lines 23-52](#23-52)

    * [Lines 90-113](#90-113)

    * [Entire file](#entire-file)

* [`Header.js`](#header-component)

* [`User.js`](#user-component)

* [Other files](#other)

# App component

The app component is the beefiest. Most importantly, this is where we declare `gapi` and `GoogleAuth` variables as global.

Once these variables are initialized, Google allows us to proceed through user flow.

`GoogleAuth` obejct:

<img src="{{site.baseurl}}/images/oauthimg1.png">

<img src="{{site.baseurl}}/images/oauthimg2.png">

Using the above format, we can access user names, emails, and confirm whether or not the user is signed in.

<hr>

# 1-13

The first 13 lines of `App.js` look like this:

```javascript
/* global gapi */
import {
  BrowserRouter as Router,
  Redirect,
  Switch,
  Route
} from 'react-router-dom';
import React, { Component } from 'react';
import './App.css';
import Header from './Header';
import User from './User';
var GoogleAuth;
var gapi;
```

While declaring that `gapi` is global in the comment on the first line works locally, it doesn't work in production. That's why line 13 declares `gpai` globally again to intialize it in the `window` object of the DOM. In addition, every time we call upon `gapi` in the code we must use `window.gapi`. 

NOTE: If you're not going to build this demo app to production, you don't have to use `var gapi;` or call `window.gapi` in the following code.

<hr>

# 14-22

Here we define the `App` class and create the constructor with state. `isAuthorized` switches to `true` when the user is sigend in. `user` holds the variable that will be shown in the user's unique URL and `userDisplay` will hold the unique users disply name in `Firstname` `Lastname` format.

```javascript
class App extends Component {
  constructor(props) {
    super(props)
    this.state = {
      isAuthorized: false,
      user: '',
      userDisplay: ''
    }
  }
```
<hr>

# 87-89

This is where we call the `loadApi()` function once React comfirms that the Component mounted successfully.

```javascript
componentDidMount() {
    this.loadApi();
}
```
<hr>

# 53-55

Now we're getting somehwere! The `loadApi()` function...LOADS THE API!

We call upon `window.gapi` for production reasons. Again - no production, no `window` necessary.

Then it uses the `.load()` method to assign the `client` as `auth2` and the second argument calls the `initClient()` function.

```javascript
loadApi = () => {
    window.gapi.load('client:auth2', this.initClient)
}
```

<hr>

# 56-86

Here's the meat and potatoes. We initialize the client with your API key and Client ID (found in your Google Dev Account)

The scope will be whatever Google API you chose to use for this project. Mine is the Google Drive API in "read only" mode.

The promise listens for an update in the sign in status (from the `updateSigninStatus()` function which simply calls the `setSigninStatus()` function), sets the sign in status, and listens for the interaction with the DOM elements via the `sign-in-or-out-button` which lives in the `Header.js` component.

Finally, `revokeAccess()` does exactly that. It gives the user the option to disconnect access from their Google account.

```javascript
initClient = () => {
    window.gapi.client.init({
      'apiKey': 'YOUR_API_KEY',
      'clientId': 'YOUR_CLIENT_ID',
      'scope': 'https://www.googleapis.com/auth/drive.metadata.readonly',
      'discoveryDocs': ['https://www.googleapis.com/discovery/v1/apis/drive/v3/rest']
    }).then(() => {
      GoogleAuth = window.gapi.auth2.getAuthInstance();
      GoogleAuth.isSignedIn.listen(this.updateSigninStatus);
      this.setSigninStatus();
      document.getElementById('sign-in-or-out-button').addEventListener('click', () => {
        this.handleAuthClick();
      });
      document.getElementById('revoke-access-button').addEventListener('click', () => {
        this.revokeAccess();
      });
    });
}
revokeAccess = () => {
    GoogleAuth.disconnect();
}
updateSigninStatus = () => {
    this.setSigninStatus();
}
```

<hr>

# 23-52

The `setSigninStatus()` is the workhorse function here. `isAuthorized` comes in from the Google API once the user has been authorized (or not) and we can set the state of the React app within this conditional. If the user is authorized, save their name and hold that value in variables we can apply to the DOM.  The `fullName` variable saves the users full name, no spaces, all lowercase so it can by applied to their unique user page URL such as `https://emilyannemoses.github.io/u/emilymoses`

This also changes the appearence of the sign in/out button, whether or not the user is signed in. It will only display the revoke-access button if the user is signed in and authorized as well. This function can be tailored to your specific needs by you.

```javascript
setSigninStatus() {
    let user = GoogleAuth.currentUser.get();
    let isAuthorized = user.hasGrantedScopes('https://www.googleapis.com/auth/drive.metadata.readonly');
    if (isAuthorized) {
      let first = user.w3.ofa
      let last = user.w3.wea
      let full = first+last
      let display = user.w3.ig
      let fullName = full.toLowerCase();
      this.setState({ 
        isAuthorized: true,
        user: fullName,
        userDisplay: display
      })
      console.log(this.state.isAuthorized)
      document.getElementById('sign-in-or-out-button').innerHTML = 'Sign out'
      document.getElementById('revoke-access-button').style.display = 'inline-block'
      document.getElementById('auth-status').innerHTML = `Welcome ${user.w3.ofa}, you are currently signed in and have granted access to this app.`
    } else {
      this.setState({
        isAuthorized: false,
        user: '',
        userDisplay: ''
      })
      console.log(this.state.isAuthorized)
      document.getElementById('sign-in-or-out-button').innerHTML = 'Sign in'
      document.getElementById('revoke-access-button').style.display = 'none'
      document.getElementById('auth-status').innerHTML = 'You have not authorized this app or you are signed out.'
    }
}
```

<hr>

# 90-113

We're bringing in `isAuthorized` from the state, which is initialized by Google's API and altered with `this.setState({})` in the `setSigninStatus()` function.

We're also saving `user` to inject the username into the URL of the `User.js` component.

In order to pass the `props` to the `User.js` component, use the `render=` attribute in the `<Route />` tag as shown.

```javascript
render() {
    const isAuthorized = this.state.isAuthorized;
    const user = this.state.user;
     return (
      <Router>
        { !isAuthorized ? (
            <Switch>
              <Route exact path="/" />
              <Redirect to="/" />
            </Switch>
          ) : (
            <Switch>
              <Route exact path={`/u/${user}`} render={(props) => <User {...props} display={this.state.userDisplay} user={this.state.user} />} />
              <Redirect from="/" to={`/u/${user}`} />
            </Switch>
          )
        }
        <Header />
      </Router>
     );
    }
}

export default App;
```

<hr>

# Entire file

```javascript
/* global gapi */
import {
  BrowserRouter as Router,
  Redirect,
  Switch,
  Route
} from 'react-router-dom';
import React, { Component } from 'react';
import './App.css';
import Header from './Header';
import User from './User';
var GoogleAuth;
var gapi;
class App extends Component {
  constructor(props) {
    super(props)
    this.state = {
      isAuthorized: false,
      user: '',
      userDisplay: ''
    }
  }
  setSigninStatus() {
    let user = GoogleAuth.currentUser.get();
    let isAuthorized = user.hasGrantedScopes('https://www.googleapis.com/auth/drive.metadata.readonly');
    if (isAuthorized) {
      let first = user.w3.ofa
      let last = user.w3.wea
      let full = first+last
      let display = user.w3.ig
      let fullName = full.toLowerCase();
      this.setState({ 
        isAuthorized: true,
        user: fullName,
        userDisplay: display
      })
      console.log(this.state.isAuthorized)
      document.getElementById('sign-in-or-out-button').innerHTML = 'Sign out'
      document.getElementById('revoke-access-button').style.display = 'inline-block'
      document.getElementById('auth-status').innerHTML = `Welcome ${user.w3.ofa}, you are currently signed in and have granted access to this app.`
    } else {
      this.setState({
        isAuthorized: false,
        user: '',
        userDisplay: ''
      })
      console.log(this.state.isAuthorized)
      document.getElementById('sign-in-or-out-button').innerHTML = 'Sign in'
      document.getElementById('revoke-access-button').style.display = 'none'
      document.getElementById('auth-status').innerHTML = 'You have not authorized this app or you are signed out.'
    }
  }
  loadApi = () => {
    window.gapi.load('client:auth2', this.initClient)
  }
  initClient = () => {
    window.gapi.client.init({
      'apiKey': 'YOUR_API_KEY',
      'clientId': 'YOUR_CLIENT_ID',
      'scope': 'https://www.googleapis.com/auth/drive.metadata.readonly',
      'discoveryDocs': ['https://www.googleapis.com/discovery/v1/apis/drive/v3/rest']
    }).then(() => {
      GoogleAuth = window.gapi.auth2.getAuthInstance();
      GoogleAuth.isSignedIn.listen(this.updateSigninStatus);
      this.setSigninStatus();
      document.getElementById('sign-in-or-out-button').addEventListener('click', () => {
        this.handleAuthClick();
      });
      document.getElementById('revoke-access-button').addEventListener('click', () => {
        this.revokeAccess();
      });
    });
  }
  handleAuthClick = () => {
    if (GoogleAuth.isSignedIn.get()) {
      GoogleAuth.signOut();
    } else {
      GoogleAuth.signIn();
    }
  }
  revokeAccess = () => {
    GoogleAuth.disconnect();
  }
  updateSigninStatus = () => {
    this.setSigninStatus();
  }
  componentDidMount() {
    this.loadApi();
  }
  render() {
    const isAuthorized = this.state.isAuthorized;
    const user = this.state.user;
     return (
      <Router>
        { !isAuthorized ? (
            <Switch>
              <Route exact path="/" />
              <Redirect to="/" />
            </Switch>
          ) : (
            <Switch>
              <Route exact path={`/u/${user}`} render={(props) => <User {...props} display={this.state.userDisplay} user={this.state.user} />} />
              <Redirect from="/" to={`/u/${user}`} />
            </Switch>
          )
        }
        <Header />
      </Router>
     );
  }
}

export default App;
```

# Header component

The `Header.js` file is where the `auth-status`, `sign-in-or-out-button` and `revoke-access-button` `id`'s live. While the file is called Header, I implemented CSS to make it look like a footer instead. You can style it however you choose by creating a `Header.css` file.

```javascript
import {
    Link
} from 'react-router-dom';
import React from 'react';
import './Header.css';

function Header() {

    return (
        <div className="Header">
            <header className="app-footer">
                <div id="auth-status" className="footer-top"></div>
                <div id="sign-in-or-out-button" className="footer">Sign in</div>
                <div id="revoke-access-button" className="footer">Revoke access</div>
                <Link to="/about" className="footer">About</Link>
                <Link to="/contact" className="footer">Contact</Link>
                <a href="http://github.com/emilyannemoses" className="footer">&copy; 2019 Emily Anne Moses</a>
            </header>
        </div>
    )
}

export default Header;
```

# User component

The `User.js` file brings in `props` from `App.js`, so it's important to follow the syntax used in the `App.js` file on the `<Route />` tag.

```javascript
import React from 'react';
import './User.css';

function User(props) {
    return (
        <div className="User">
            <h1>User Component</h1>
            <h2>Welcome {props.display}</h2>
        </div>
    )
}

export default User;
```

# Other

`index.html` file should look like so:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <!--
      manifest.json provides metadata used when your web app is installed on a
      user's mobile device or desktop. See https://developers.google.com/web/fundamentals/web-app-manifest/
    -->
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <!--
      Notice the use of %PUBLIC_URL% in the tags above.
      It will be replaced with the URL of the `public` folder during the build.
      Only files inside the `public` folder can be referenced from the HTML.
      Unlike "/favicon.ico" or "favicon.ico", "%PUBLIC_URL%/favicon.ico" will
      work correctly both with client-side routing and a non-root public URL.
      Learn how to configure a non-root public URL by running `npm run build`.
    -->
    <title>OAuth-React App</title>
    <script src="https://apis.google.com/js/api.js" async defer></script>
    <script src="https://apis.google.com/js/platform.js?onload=init" async defer></script>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```

`package.json` should look like so:

```json
{
  "name": "oauth-test",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^16.8.6",
    "react-dom": "^16.8.6",
    "react-router": "^5.0.1",
    "react-router-dom": "^5.0.1",
    "react-scripts": "3.0.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}
```

Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Want to tackle <a href="https://twitter.com/googleapi?ref_src=twsrc%5Etfw">@googleapi</a>&#39;s Client Side OAuth 2.0 with <a href="https://twitter.com/reactjs?ref_src=twsrc%5Etfw">@reactjs</a>? I laid it all out (more or less) in this article<br><br>***<a href="https://twitter.com/hashtag/e4everything?src=hash&amp;ref_src=twsrc%5Etfw">#e4everything</a> <a href="https://twitter.com/hashtag/googleoauth?src=hash&amp;ref_src=twsrc%5Etfw">#googleoauth</a> <a href="https://twitter.com/hashtag/learntocode?src=hash&amp;ref_src=twsrc%5Etfw">#learntocode</a> <a href="https://twitter.com/hashtag/javascript?src=hash&amp;ref_src=twsrc%5Etfw">#javascript</a> <a href="https://twitter.com/hashtag/WomenWhoCode?src=hash&amp;ref_src=twsrc%5Etfw">#WomenWhoCode</a> <a href="https://twitter.com/hashtag/reactjs?src=hash&amp;ref_src=twsrc%5Etfw">#reactjs</a> <a href="https://twitter.com/hashtag/webdev?src=hash&amp;ref_src=twsrc%5Etfw">#webdev</a> <a href="https://twitter.com/hashtag/codinglife?src=hash&amp;ref_src=twsrc%5Etfw">#codinglife</a> <br><br>***<a href="https://t.co/ev5RtXaJLM">https://t.co/ev5RtXaJLM</a> <a href="https://t.co/HgCL6mMoUi">pic.twitter.com/HgCL6mMoUi</a></p>&mdash; Emily Anne Moses (@emilyannemoses) <a href="https://twitter.com/emilyannemoses/status/1140994681318334467?ref_src=twsrc%5Etfw">June 18, 2019</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<span><a href="https://emilyannemoses.github.io/blog/2019/06/17/basics-pt2.html" style="float:left;">Previous: Basics - Part 2</a><a href="https://emilyannemoses.github.io/blog/2019/06/21/repetition-structures.html" style="float:right;">Next: Repetition Structures</a></span>

[oauth]: https://developers.google.com/identity/protocols/OAuth2UserAgent
[react]: https://reactjs.org/