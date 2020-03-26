<p align="center"><a href="https://lyduz.com" target="_blank" rel="noopener noreferrer"><img width="200" src="https://lyduz.com/logo-dark.svg" alt="Vue logo"></a></p>

## Frontend Development Guidelines
A document that contains **Nuxt**, **Vue**, **Javascript**, **CSS** & **HTML** standards, examples, and best practices that shall be followed when writing code.

This is to ensure that code we produce is uniform, maintainable, scalable and can be easily understood by other developers in the team.

## Javascript
- Function names must be written in camelCase.
  ``` javascript
  sendRequest() {
    console.log("Send noods (noodles).");
  }
  ```
- Variable names must be written in  camelCase.
  ``` javascript
  const firstName = 'Ses';
  ```
 - Every function written must have documentation. It can include when this function is called and what the function does. There is a VSCode extension that simplifies this process ( **VS DocBlockr** ).
   ```javascript 
   /**
   * Fires when user clicks 'Bullish' button, sends API request and 
   * emits 'Increment' to parent component.
   *
   * @param   {string}  userId
   *`
   * @return`
   */
   bullish() { ... } 
   ```
- All ``console.log()`` should be omitted before pushing.
- As of **ECMAScript 6** the recommended syntax for writing functions is:
`` sendRequest() { } `` instead of ``function sendRequest() { }``
- As of **ECMAScript 6** ``let`` and ``const`` are the recommended variable keywords instead of ``var``. Read [why.](https://hacks.mozilla.org/2015/07/es6-in-depth-let-and-const/)
- Comments in code should only be either: documentation or TODO's. Remove unnecessary comments such as console logs or commented out variables before pushing.

- Remove unnecessary/unused code before pushing. Empty lifecycle hooks shall be omitted too.

## Vue / Nuxt
- File names of Vue Components must be written in PascalCase
 	> MiniWatchlist.vue

- URLs should not be hard coded and shall be stored at our **.env** files. This is to simplify the process of changing those values.
  ```
  const baseURL = process.env.API_URL; //Yes!~

  const baseURL = "https://dev-api.arbitrage.ph/api"; //No!
  ```
-	The order of our Nuxt templates shall be template -> script -> style with a newline separator after each element:
    ``` html
    <template> </template>

    <script> </script>

    <style> </style>
- When dealing with objects that need to be iterated and displayed (List Rendering), the recommended syntax is: 
  ``` javascript
  <v-card v-for="(post, index) in postsObject" :key="index">
  
  	/* In this case, the currently iterated value 
      will be in the 'post' variable */
      
     <span> My name is {{post.name}} </span>
  </v-card>
  ```


## CSS & Vuetify
 - If a color value is frequently used such as ``#03DAC5``, it must be added to our **nuxt.config.js** and assigned a variable. Avoid hard coding of frequently used hex code colors.

 - Class names shall follow the [BEM](http://getbem.com/) methodology.
   ```
   .bearish__button--active
   ```
- Do not use **!important** properties if possible. Especially on element selectors such as ``div`` ``a`` ``span``, etc. If you need to use **!important** be sure to wrap it first in your custom class name to not affect other elements.
  ```
  .bearish__button .v-btn span { }
  ```
- Do not add custom properties to **Vuetify** generated classes. If you have to, consult and inform all other frontend devs of this to discuss if this will break other UI designs currently existing. For example, **DO NOT DO THIS:**
  ``` 
   .v-menu__content > .v-select-list > .v-list {
    padding: unset;
    border: 1px solid #172431;
  }
  ```
- If possible, scope your CSS to the current component.
  ```
  <style scoped>
  ```
