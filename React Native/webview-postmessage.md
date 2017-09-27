# Webview with postMessage 

Annoying bug when using window.postMessage on WebView, it shows red screen in dev or crash in release mode. There are several ways to fix it. The solution below is one of those ways that doesn't change node_modules folder.

```javascript

const patchPostMessageFunction = function() {
  var originalPostMessage = window.postMessage;

  var patchedPostMessage = function(message, targetOrigin, transfer) {
    originalPostMessage(message, targetOrigin, transfer);
  };

  patchedPostMessage.toString = function() {
    return String(Object.hasOwnProperty).replace(
      "hasOwnProperty",
      "postMessage"
    );
  };

  window.postMessage = patchedPostMessage;

  // your code here
};

const patchPostMessageJsCode = "(" + String(patchPostMessageFunction) + ")();";

const patchPostMessageFunctionModal = function() {
  var originalPostMessage = window.postMessage;

  var patchedPostMessage = function(message, targetOrigin, transfer) {
    originalPostMessage(message, targetOrigin, transfer);
  };

  patchedPostMessage.toString = function() {
    return String(Object.hasOwnProperty).replace(
      "hasOwnProperty",
      "postMessage"
    );
  };

  window.postMessage = patchedPostMessage;
};

const patchPostMessageJsCodeModal =
  "(" + String(patchPostMessageFunctionModal) + ")();";

class Foo extends Component {
    render () {
        <WebView
            injectedJavaScript={patchPostMessageJsCode}
            onMessage={this.onMessage}
            source={{uri: this.state.uri}}
        />
    }
}
```