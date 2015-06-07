SimpleHUD
=========

SimpleHUD is an easy-to-use yet beautiful HUD for android.

![截图](https://raw.githubusercontent.com/wangvsa/SimpleHUD/master/screenshots/screenshot.png)

## Installation

1. Clone or download SimpleHUD if you haven't yet.
2. Import SimpleHUD project.
3. Add SimpleHUD as a dependency to your existing project and you're good to go.

## Usage

(See sample project in /SimpleHUDDemo)

The HUD is created as singleton so you can just use a static method like `showSuccessMessage()` to show a HUD.
If there's an existing HUD, it will be dismissed and show the new one.

### Showing the loading dialog

```java
SimpleHUD.showLoadingMessage(this, "loading data, please wait...", true);
```

Note the third parameter `boolean cancelable`, if you set it to `true` then you can tap the back button to cancel the HUD.

When your operation is completed, call `dismiss()` method to dismiss it.
```java
SimpleHUD.dismiss();
```

### Showing the message dialog

The next three HUD are the same except the icon.
It will dismiss itself so no need to to invoke `dimiss()` explicitly.

```java
SimpleHUD.showInfoMessage(this, "This is a info message.");
SimpleHUD.showErrorMessage(this, "This ia an error message.");
SimpleHUD.showSuccessMessage(this, "This ia a success message.");
```

### Invoke your method when the HUD dimisses

Create an object of the  `SimpleHUDCallback` interface and implement its `onSimpleHUDDismissed` method.
Then pass it to SimpleHUD as an argument. Here's an example:

```java
private SimpleHUDCallback simplehudCallback = new SimpleHUDCallback() {
  @Override
  public void onSimpleHUDDismissed() {
    startHomeActivity();
  }
};
SimpleHUD.showInfoMessage(this, "This is a info message.", simplehudCallback);
// SimpleHUD.showErrorMessage(this, "This ia an error message.", simplehudCallback);
// SimpleHUD.showSuccessMessage(this, "This ia a success message.", simplehudCallback);
```


## Customization

### Change the display time

Set the variable `dismissDelay` to one of the three constants.
```java
SimpleHUD.dismissDelay = SimpleHUD.DISMISS_DELAY_SHORT;     // 2s
SimpleHUD.dismissDelay = SimpleHUD.DISMISS_DELAY_MIDIUM;    // 4s
SimpleHUD.dismissDelay = SimpleHUD.DISMISS_DELAY_LONG;      // 6s
```

Or a arbitrary value.
```java
SimpleHUD.dismissDelay = 8000;                              // 8s
```

### Change the icon

There are three icons in drawable folder, you can replace them using your own icons with the same name.
