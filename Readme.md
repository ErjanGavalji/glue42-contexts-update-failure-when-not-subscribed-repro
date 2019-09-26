Glue42 Contexts Update Failure When Not Subscribed For Updates Repro
====

# Description
A repro for:
- The scenario of the Context Viewer not showing a new context item
- The scenario of calling `glue.contexts.update()` when not subscribed to the
changes

# Run

## Scenario 1: Context Viewer not showing a new context item
1. Get the repository
2. run `npm install` within the root folder
3. run `npm run dev` within the root folder
4. Launch Glue42
5. Use `ALT+CLICK` on AppManager to view all apps
6. Launch Context Viewer form AppManager
7. Use the *Open* option from the Glue42 taskbar icon context menu to start
`http://localhost:8872`
8. Hit the *Set Context!* button to set a new context
9. Check the Context Viewer.

> Expected: The Context Viewer should contain a new context item, named
> `MyNewContext`
> Actual: but it does not. It will only show it after a refresh.

## Scenario 2: Context update failure
1. Get the repository
2. run `npm install` within the root folder
3. run `npm run dev` within the root folder
4. Launch Glue42
5. Use the *Open* option from the Glue42 taskbar icon context menu to start
`http://localhost:8872`
6. Use the Settings dialog of the Glue42 toolbar to change the theme to **Day**
7. Hit the *Set Theme!* button of the repro app to change the theme to **Night**
8. Use the Settings dialog of the Glue42 toolbar to change the theme to **Day**
again
9. Hit the *Set Theme!* button of the repro app

> Expected: Theme to be changed to night again
> Actual: Theme not changed

> Hint: If we subscribe for the context updates, then we will have it working!
> See the line `glue.contexts.subscribe(...)`;