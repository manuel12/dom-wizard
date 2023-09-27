# DOM Manipulation Library

A JavaScript library that allows easy manipulation of the DOM. 

Click [here]() to read more about the features.

## Examples

Here's how you can create an element and append it to the DOM:

```javascript
import domManager from '@dom-manipulation-library/dml'

const sidebar = () => {
    const upper = {
        tagName: "div",
        options: {
            classList: ["upper", "nv-class"],
        },
    };

    const lower =  {
        tagName: "span",
        options: {
            className: "lower",
            style: { color: "#0f0" },
        },
    };

    return {
        tagName: "div",
        options: {
            id: "sidebar"
        },
        children: [upper, lower],
    };
}

domManager.create(sidebar());
```

This allows you to easily create elements and their children using simple objects. 

To read more about the features, jump to the [features section]().


## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement". Don't forget to give the project a star! Thanks again!

1. [Fork](https://github.com/lindelwa122/dom-manipulation-library/fork) this repository.

2. Clone the repository to your own machine by running one of the following commands:

    * HTTPS
    ```
    git clone https://github.com/<your-username>/dom-manipulation-library.git
    ```

    OR 

    * SSH
    ```
    git clone git@github.com:<your-username>/dom-manipulation-library.git
    ```

    OR

    * Github CLI:
    ```
    gh repo clone <your-username>/dom-manipulation-library
    ```

3. Create a new branch. The name of the branch must reflect the change you are about to make.

    ```
    git checkout -b <branch-name>
    ```

4. Make your changes or add your new feature. Remember to commit early and commit often. Read our commit rules [here](). 

    * Short commit messages:
        ```
        git add <changed-files>
        git commit -m "<commit-message>"
        ```
    * Long commit messages:
         ```
        git add <changed-files>
        git commit
        ```

5. Push your changes to Github by running this command:
    ```
    git push origin <branch-name>
    ```

6. Go over to GitHub and create a pull request. Ensure to add a comment explaining what you added. For more info read our contributing rules [here]().

## Features

These are the features the library will have, most of the following aren't built yet and we need you to help us. To read more about each feature click on the subtitle. You can also indicate on the issues tab that you are working on a specific feature even though this is not required. Click [here]() ti read more about our contributing rules.

### domManager

The main idea of the library was to create something that can allow developers to create, update, modify, and delete the DOM elements with ease. The whole job of **domManager** is to do just that.

I wrote the code below a few months ago and it is to show you how hard and error-prone it can be to manually append and modify elements to the DOM.

```javascript
for (account of accounts) {

    if (account["result"] == "empty") {
        card = document.createElement("div");
        card.classList = "card";
        text = document.createTextNode("Not Found");
        card.appendChild(text);
        display.appendChild(card);
        return;
    }
                
    card = document.createElement("div");
    card.classList = "card";
    card.setAttribute("onclick", "cardClicked(event)"); 
    content = document.createElement("div");
    content.classList = "content";
    img = document.createElement("img");
    img.src = "static/uploads/" + account["image"];
    span = document.createElement("span");
    username = document.createTextNode(account["username"]);
    span.appendChild(username);
    content.appendChild(img);
    content.appendChild(span);
    extraContent = document.createElement("div");
    extraContent.classList = "extra-content";
    date = document.createTextNode(calcDate(account["started_on"]) + "/" + calcChallenge(account["level"]));
    extraContent.appendChild(date);
    card.appendChild(content);
    card.appendChild(extraContent);
    display.appendChild(card);
}
```

The same thing can be done with ease using the 4 functions that **domManager** will have:

- [ ] **create**
- [ ] **update**
- [ ] **read**
- [ ] **delete**

The functions will do exactly as what their names portray, they will provide functionality to create, update, delete, and read elements. Click [here]() to read more about they should work.

### Router

**Router** will allow developers to navigate to different routes of the site without the page reloading.

Here's an example of how easy it could be to use this feature in your app.

***router.js***
```javascript
import home from './routes/home';
import about from './routes/about';
import contacts from './routes/contact';

const routes = [
    { id: 'homePage', route: home, url: 'home' },
    { id: 'aboutPage', route: about, url: 'about' },
    { id: 'contactsPage', route: contacts, url: 'contacts' },
];

export default routes;
```

Here's how you can register routes and navigate to another page.

***index.js***
```javascript
import domManager, { router } from '@dom-manipulation-library/dml'
import routes from './routes/router';

const initialPage = {
    tagName: "button",
    options: {
        route: "aboutPage", // look here
        innerHTML: "Click Me - About"
    }
}

domManager.create(initialPage);
router.register(routes);
```

Above we create an initial page with nothing but just a button that says `Click Me - About`. If you click on this button you will be taken to the about page. `route` in the options expects an ID of a certain route.

Let's take a look at the functions that will make this magic happen:

- [ ] **register**: This function will register all the routes as it did on the above example.
- [ ] **configRoute**: This a helper function that **domManager** will invoke when it finds the property `route` in `options`.
- [ ] **activate**: This is a private function that is supposed to add a className of active to the clicked element. 
- [ ] **deactivate**: A private function that removes the className of active.

To gain a better understand of the above functions click [here]().
     
 ### createStyleSheet

 Here's how you can use **createStyleSheet** to style content of your page: 

 ```javascript
import { createStyleSheet } from '@dom-manipulation-library/dml'

createStyleSheet.createCSSRule({
    'body': {
        color: '#f8f8f8',
        backgroundColor: '#0fa',
    },

    '#main > .content': {
        overflow: 'hidden',
    },
})
 ```   

- [ ] **createCSSRule**: Takes in an object with selectors and declarations and styles the elements.
- [ ] **createMediaQueryRule**
- [ ] **configStateRule**: Adds a style to an element depending on its state.
- [ ] **createStyle**: Adds a style to an element.

To gain a better understanding of how these functions should work click [here]().

### store

The store will store variables that are supposed to accessible throughout the app. The user can be able to retrieve, modify these variable from anywhere in the app.

- [ ] **createStore**: creates all the variables in their initial state.
- [ ] **getState**: gets the state of a variable.
- [ ] **updateState**: modifies state.

Read more about how store should work [here]().