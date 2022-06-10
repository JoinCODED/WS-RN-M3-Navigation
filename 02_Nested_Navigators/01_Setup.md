1. Let's create 2 components, one to show `DC` and another to show `Marvel`.

```js
const DcMovies = ({ navigation }) => {
  const moviesList = moviesStore
    .getMovies()
    .filter((movie) => movie.from === 'DC')
    .map((movie) => (
      <TouchableOpacity
        key={movie.id}
        onPress={() => navigation.navigate('MovieDetail', { id: movie.id })}
      >
        <Image source={movie.image} style={styles.image} />
      </TouchableOpacity>
    ));

  return (
    <View style={styles.container}>
      <ScrollView>
        <View style={styles.header}>
          <Image
            source={require('../assets/mainimage.jpg')}
            style={{ width: 350, height: 150 }}
          />
        </View>

        <Text style={styles.text}>DC Movies</Text>

        <View style={styles.grid}>{moviesList}</View>
      </ScrollView>
    </View>
  );
};

export default DcMovies;
```

Its almost the same component but we are filtering the movies that are from `DC`.

Do the same for `Marvel` movies.
