1. In the RN Debugger, you can see that `props` received by the `Home` component has something called `navigation` which has all the functions we need. This is the super power of React Navigation.

2. To navigate from one screen to another, we will use the `navigate` method of the `props.navigation` object.

3. In `MovieList.js`, receive `{navigation}` as a `prop`.

   ```javascript
    const MoviesList = ({ navigation }) => {
   ```

4. Wrap each movie with a `TouchableOpacity`.

   ```javascript
   const moviesList = moviesStore.getMovies().map((movie) => (
     <TouchableOpacity key={movie.id}>
       <Image source={movie.image} style={styles.image} />
     </TouchableOpacity>
   ));
   ```

5. But what will we pass to `navigate`? The `name` of the screen we want to navigate to. Keep in mind that it has to be a string.

   ```javascript
   const moviesList = moviesStore.getMovies().map((movie) => (
     <TouchableOpacity
       key={movie.id}
       onPress={() => navigation.navigate('MovieDetail')}
     >
       <Image source={movie.image} style={styles.image} />
     </TouchableOpacity>
   ));
   ```

   Note that the navigation is animated, it affects the header by adding a back button which actually works, and you can go back using gestures! The magic of React Navigation!!!
