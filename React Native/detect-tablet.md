### Detect iPad without custom native module 

We have __react-native-device-info__ with method __isTablet__, but in case we can't touch custom native module (Expo). Here is the way:
```javascript
import { Dimensions } from 'react-native';
const {height, width} = Dimensions.get('window'); 
const aspectRatio = height/width;

if(aspectRatio>1.6) {

   // Code for Iphone

}
else {

   // Code for Ipad

}
```