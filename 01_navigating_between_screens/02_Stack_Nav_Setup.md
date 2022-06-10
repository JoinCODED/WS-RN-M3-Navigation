1. Install `react-navigation/stack`.

   ```bash
   $ npm install @react-navigation/stack
   ```

2. Import `createStackNavigator` from `react-navigation/stack`

   ```javascript
   import { createStackNavigator } from '@react-navigation/stack';
   ```

3. Now we'll call `createStackNavigator` **outside** the `App` component, and save it in a variable called `Stack`. Let's console log it to see what's inside it.

   ```javascript
   const Stack = createStackNavigator();
   console.log('App -> Stack', Stack);
   ```

   `createStackNavigator` returns an object that has two properties, `Navigator` and `Screen`. Both `Navigator` and `Screen` are components.

4. Let's de-structure Stack.

   ```javascript
   const { Navigator, Screen } = createStackNavigator();

   export default function App() {
       ...
   }
   ```

5. Wrap `MovieList` with `Navigator`.

   ```javascript
   export default function App() {
     return (
       <NavigationContainer>
         <Navigator>
           <MovieList />
         </Navigator>
       </NavigationContainer>
     );
   }
   ```

   This will give us an error. We can't render components directly inside a `Navigator` component.

6. To define a component as a screen, we will render `Screen` and pass the component as a `prop`. Every `Screen` must be given a name as well.

   ```javascript
   export default function App() {
     return (
       <NavigationContainer>
         <Navigator>
           <Screen name="Home" component={MovieList} />
         </Navigator>
       </NavigationContainer>
     );
   }
   ```

   Let's take a look. Yes! It's working! And what's this? We got a header without asking for one! How cool is that?

7. Let's create a component called `MovieDetail` in the components folder.

```js
import { observer } from 'mobx-react';
import * as React from 'react';
import { View, Text, ScrollView, Image, StyleSheet } from 'react-native';
import moviesStore from '../stores/moviesStore';

const MovieDetail = () => {
  const movie = moviesStore.getMovieById(1);
  return (
    <View style={styles.container}>
      <ScrollView>
        <View style={styles.header}>
          <Image source={movie.image} style={{ width: 350, height: 150 }} />
        </View>

        <Text style={styles.text}>{movie.title}</Text>
        <Text style={styles.text}>{movie.description}</Text>
      </ScrollView>
    </View>
  );
};

export default observer(MovieDetail);

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  image: {
    marginTop: 15,
    height: 200,
    borderRadius: 10,
  },
  text: {
    marginTop: 20,
    fontWeight: 'bold',
    fontSize: 20,
    marginLeft: 10,
  },

  header: {
    flexDirection: 'row',
    justifyContent: 'center',
    alignItems: 'center',
    marginTop: 25,
  },
});
```

for now, we will always get movie id 1.

8. Let's create the `getMovieById` function in the `moviesStore` file.

   ```js
   getMovieById = (id) => {
     return this.movies.find((movie) => movie.id === id);
   };
   ```

9. Let's add more screens.

   ```javascript
   export default function App() {
     return (
       <NavigationContainer>
         <Navigator>
           <Screen name="Home" component={Home} />
           <Screen name="MovieDetail" component={MovieDetail} />
         </Navigator>
       </NavigationContainer>
     );
   }
   ```

10. How can we choose which screen appears first? We will pass `Navigator` a `prop` called `initialRouteName` and pass it the `name` of the screen we want to be first.

    ```javascript
        <NavigationContainer>
          <Navigator initialRouteName="Home">
    ```
