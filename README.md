# EasyCEF: Installation and Notes

This resource adds a simplified system for creating HTML browsers, as well as other features such as forcing the cursor to display.

## Requirements
* RAGE Multiplayer 1.1 and above

## Installing
* Put the folder into 'client_packages' (client_packages/easycef).
* Add require('easycef') to 'client_packages/index.js'.

## Clientside API
```js
/**
 * Creates Browser and pushes it into instances array with given parameters.
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @param {string} browserPath			Browser Path / starts from client_packages (example: "testcef/index.html").
 * @param {bool} forceToCursor			Forces the game to display the cursor, even if the player can disable it until the browser is destroyed again.
 */
mp.game.app.createBrowser(browserName, browserPath, forceToCursor);


/**
 * Destroys Browser and removes it from instances array.
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 */
mp.game.app.destroyBrowser(browserName);


/**
 * Switches browser (destroys old browser and creates new one with same name).
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @param {string} newPath				Browser Path / starts from client_packages (example: "testcef/index.html").
 * @param {bool} forceToCursor			Forces the game to display the cursor, even if the player can disable it until the browser is destroyed again.
 */
mp.game.app.switchBrowser(browserName, newPath, forceToCursor);


/**
 * Reloads the browser.
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @param {bool} ignoreCache			True to ignore cache.
 */
mp.game.app.reloadBrowser(browserName, ignoreCache);


/**
 * Calls JavaScript code inside the browser.
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @param {string} codeToExecute		JavaScript code to be executed in browser.
 */
mp.game.app.executeClientFunction(browserName, codeToExecute);


/**
 * Set cursor in a specific browser forced or unforced.
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @param {bool} force					True to force the cursor to be there.
 */
mp.game.app.setCursorForced(browserName, force);


/**
 * Returns is the cursor forced in browser
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @return {bool} 						True if forced, otherwise false.
 */
mp.game.app.isCursorForcedInBrowser(browserName);

/**
 * Returns is a cursor forced in any browser.
 * @return {bool} 						True if any cursor is forced, otherwise false.
 */
mp.game.app.isAnyCursorForced();


/**
 * Returns the specified item.
 * @param {string} browserName			Browser identifier (example: "TestBrowser1").
 * @return {object} 					The function will return nothing if browser does not exist.
 */
mp.game.app.getBrowserObject(browserName);
```

## Notes

* With 'isAnyCursorForced' you can work for example by checking in your cursor keybind function if a cursor is forced in any CEF.
* For any error messages or questions: Feel free to write me on Discord: мαяνιη.#9554
* Not all RAGE browser functions are implemented yet, should be relatively easy to add, maybe an update will come soon
* There is a 'better cursor' system implemented that automatically shows the cursor if there is a browser that forces it. If you want to disable it and build your own, just set 'isBetterCursorEnabled' in the file to **false**.
