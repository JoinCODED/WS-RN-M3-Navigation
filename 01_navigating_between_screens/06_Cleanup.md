There's a lot going on in `App.js`, so let's refactor the whole stack navigator into its own component, in its own folder.

1. Create a folder in `components` called `Navigation` with an `index.js` file.

2. We will call the component `RootNavigator`. Setup your component.

   ```javascript
   const RootNavigator = () => {};
   ```

3. Move the `Navigator` component and everything inside it to `index.js`. Don't forget to move all the imports.

4. Import `RootNavigator` in `App.js` and render it under `NavigationContainer`.

   ```javascript
   <NativeBaseProvider>
     <NavigationContainer>
       <RootNavigator />
     </NavigationContainer>
   </NativeBaseProvider>
   ```
