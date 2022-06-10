Starting point: fork and clone this [repository](https://github.com/JoinCODED/Demo-RN-M3-Navigation)

We need to install a few dependencies to use [React Navigation](https://reactnavigation.org/docs/getting-started/).

1. Install `react-navigation/native`.

   ```bash
   $ npm install @react-navigation/native
   ```

2. Install expo dependencies. The reason why we use `expo` instead of `npm` is that Expo will download the version of those dependencies that are compatible with your apps.

   ```bash
   $ expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
   ```

3. Let's refactor our code a bit, and create a `moviesList` component and move our code there.

```js
const MoviesList = ({ navigation }) => {
  const moviesList = moviesStore
    .getMovies()
    .map((movie) => <Image source={movie.image} style={styles.image} />);

  return (
    <View style={styles.container}>
      <ScrollView>
        <View style={styles.header}>
          <Image
            source={require('../assets/mainimage.jpg')}
            style={{ width: 350, height: 150 }}
          />
        </View>

        <Text style={styles.text}>Movies</Text>

        <View style={styles.grid}>{moviesList}</View>
      </ScrollView>
    </View>
  );
};

export default MoviesList;
```

Make sure to also move the styles to the `moviesList` component and fix your imports.

4. In `App.js`, Import `moviesList` and wrap it with `NavigationContainer`, which is imported from `react-navigation`.

   ```javascript
   import { NavigationContainer } from "@react-navigation/native";

   [...]

   export default function App() {
    return (
      <NavigationContainer>
        <MoviesList />
      </NavigationContainer>
    );
   }
   ```
