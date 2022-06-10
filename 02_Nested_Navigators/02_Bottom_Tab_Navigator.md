1. Install the `BottomTabNavigator` into your project.

```shell
$ npm install @react-navigation/bottom-tabs
```

2. In your `Navigation` folder, create a new file called `TabNavigator.js`.

3. Import `createBottomTabNavigator` and setup your component.

```javascript
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

function TabNavigator() {
  return ();
}

export default TabNavigator;
```

4. Call `createBottomTabNavigator` that we just imported and assign it to a constant called `Tab`.

```javascript
const Tab = createBottomTabNavigator();
```

5. Now we will create our tab navigator in our component.

```javascript
function TabNavigator() {
  return (
    <Tab.Navigator>
    </Tab.Navigator>
  );
```

6. Every Navigator in react native comes with a default header, and we already have one from our old stack navigator, so we will end up with two headers. So we need to pass a `screenOptions` to our tab navigator and set `headerShown` to `false`.

```javascript
function TabNavigator() {
  return (
    <Tab.Navigator
      screenOptions={{
        headerShown: false,
      }}
    >
    </Tab.Navigator>
  );
```

7. Now let's start adding our tabs, the first tab will be our stack navigator, hence why it's called nested navigator, because we have a `stack` navigator nested in a `tab` navigator. you can do it the other way around, nested `tab` into a `stack`, `stack` into a `drawer`, or whatever your app needs.

```javascript
<Tab.Screen name="Home" component={RootNavigator} />
```

8. It doesn't make sense to call it `RootNavigator` anymore. Because our RootNavigator will be our new `TabNavigator`. Rename it to `StackNavigator` for example.

```javascript
<Tab.Screen name="Home" component={StackNavigator} />
```

9. You can add a label and an icon to this tab by adding `options` to this tab screen and passing it a `tabBarLabel` and a `tabBarIcon`.

```js
import Ionicons from '@expo/vector-icons/Ionicons';
```

```javascript
<Tab.Screen
  name="Home"
  component={RootNavigator}
  options={{
    tabBarLabel: 'Home',
    tabBarIcon: ({ color, size }) => (
      <Ionicons name="md-home" size={size} color={color} />
    ),
  }}
/>
```

10. Our other tab will be `DC` movies page that we created before.

```javascript
<Tab.Screen
  name="DC"
  component={DcMovies}
  options={{
    tabBarLabel: 'DC',
    tabBarIcon: ({ color, size }) => (
      <Ionicons name="md-film" size={32} color={color} />
    ),
  }}
/>
```

11. And the last one will be `Marvel` movies page that we created before.

```js
<Tab.Screen
  name="Marvel"
  component={MarvelMovies}
  options={{
    tabBarLabel: 'Marvel',
    tabBarIcon: ({ color, size }) => (
      <Ionicons name="md-film" size={32} color={color} />
    ),
  }}
/>
```

12. The last thing we need to do, is to navigate into our `App.js` and changing the main navigator from the old `stack` to our new `tab` navigator.

```javascript
export default function App() {
  return (
    <NavigationContainer>
      <TabNavigator />
    </NavigationContainer>
  );
}
```
