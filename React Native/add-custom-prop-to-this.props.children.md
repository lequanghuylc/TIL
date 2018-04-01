# Add custom props to this.props.childrend

```javascript
{ 
  React.Children.map(children, (child, i) =>
  React.cloneElement(child, { foo: "bar" })) 
}
```