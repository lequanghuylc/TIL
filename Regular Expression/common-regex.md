### Find text between KEYWORD1 and KEYWORD2
```
/KEYWORD1((.(?!KEYWORD1))+?)KEYWORD2/g
```


### Validate Url
```javascript
const re = /^(http[s]?:\/\/){0,1}(www\.){0,1}[a-zA-Z0-9\.\-]+\.[a-zA-Z]{2,5}[\.]{0,1}/;
re.test(url) // true or false
```