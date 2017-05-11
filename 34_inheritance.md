# 3.4 Inheritance

The style rules themselves will probably seem very familiar to you from CSS, but one thing that works very differently is style inheritance.

By default Components will not inherit any styles. The style property can be a plain object, or it can be an array of styles. The last style has precedence, so that's one thing you can use to avoid style duplication.

```javascript
const paragraphStyle = {
  color: 'grey',
  fontSize: 30,
};

function MyComponent() {
  return (
    <Text style={[paragraphStyle, { fontSize: 40}]}>
      Hello World
    </Text>
  );
}
```

But let's take it a step further than that. Instead of relying on a list of styles, we can use component composition to create styled component primitives.

Under this approach, instead of using a Text component and adding your styles, you'd import the BodyText component from your styleguide and use that directly. That way your component will have some base styles, but it allows them to be overriden by any styles passed directly as props.

```js
function BodyText(props) {
  return <Text ...props style=[paragraphStyle, props.style]>{props.children}</Text>;
}

// usage

<BodyText style={{ textAlign: 'center' }} some="value" }>Hello there</BodyText>

// you can also layer these components on each other
// for example by defining a Heading1 as a BodyText with a larger fontSize

function Heading1(props) {
  return <BodyText ...props style=[{ fontSize: 40 }, props.style]}>{props.children}</BodyText>;
}
```



