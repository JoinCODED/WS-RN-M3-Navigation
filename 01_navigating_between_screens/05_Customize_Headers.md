1. At this point, the header's title is the screen's name. But how can we give it a different name? We will pass `Screen` another `prop` called `options` which takes an object, where we can change the title.

   ```jsx
   <Screen
     name="Home"
     component={MoviesList}
     options={{ title: 'Pick a movie' }}
   />
   ```

2. This `options` object is so cool, we can customize a screen's header. Let's give it a cool color.

   ```jsx
   <Screen
     name="Home"
     component={MoviesList}
     options={{
       headerStyle: {
         backgroundColor: '#ffd1dc',
       },
     }}
   />
   ```

   Or we can remove the header from `Home` screen entirely by setting `headerShown` to `false`!

   ```jsx
   <Screen
     name="Home"
     component={MoviesList}
     options={{ headerShown: false }}
   />
   ```

3. Now for `Movie Detail` we want the header title to be dynamic. It should be the movie's name. So to access the movie name, we will pass `options` a function, this function takes `props` as an argument. We will destruct it to access `route`, then we will pass the `id` of the `movie` saved in `route.params` to `title` as a return value.

   ```jsx
   <Screen
     name="MovieDetail"
     component={movieDetail}
     options={({ route }) => {
       const { id } = route.params;
       return {
         title: moviesStore.getMovieById(id).title,
       };
     }}
   />
   ```

4. To customize the header for **all** components we will pass `Navigator` a `prop` called `screenOptions` which takes an object and you can customize your header the way you want.

   ```jsx
   <Navigator
     initialRouteName="Home"
     screenOptions={{
       headerTintColor: "white",
       headerStyle: {
         backgroundColor: "#90d4ed",
       },
       headerTitleStyle: {
         fontWeight: "bold",
       },
     }}
   >
   ```

   This becomes the default header for all screens. Any customization on the `Screen` component level will override this `Navigator`-level header customization.
