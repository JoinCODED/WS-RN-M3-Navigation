Now when we navigate to a movie, we should see its description.

What we need to do is pass the id of the movie object to `MovieDetail`.

1. In `MovieList` we will pass `navigate` another argument which is an object, the key is the name of your route param and the value is whatever you want to pass.

   ```javascript
   const moviesList = moviesStore.getMovies().map((movie) => (
     <TouchableOpacity
       key={movie.id}
       onPress={() => navigation.navigate('MovieDetail', { id: movie.id })}
     >
       <Image source={movie.image} style={styles.image} />
     </TouchableOpacity>
   ));
   ```

   How can we receive it in `MovieDetail`? Let's check `props` again in RN Debugger, you'll see that its saved in `route.params`.

2. So we will destruct `props` and receive `route`, then from `route` we will take the value of `id`.

   ```javascript
   const MovieDetail = ({ route }) => {
   const { id } = route.params;
    const movie = moviesStore.getMovieById(id);
   ```

3. Let's check our app again. Yes! It works!
