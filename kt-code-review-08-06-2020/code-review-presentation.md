---
theme: 'night'
transition: 'slide'
highlightTheme: 'monokai'
logoImg: '/img/logo.png'
slideNumber: false
title: 'Code Review on Android Projects'
---

<!-- Styles-->
<style>
  .container{
    display: flex;
  }
  .col{
      flex: 1;
  }
</style>

<!--Template used https://raw.githubusercontent.com/evilz/vscode-reveal/master/sample.md -->

### Code Review

_on Android Projects_

<small> 
  <strong>DG Conference Week</strong> <br /><br />
  Created by <i>Gabriel B. Moro - <a>moro@devgrid.co.uk</a></i> <br />
  </small>

---

### Summary

- Performance

- Aesthetics

- Dirt Code

- Accessibility

- Dangerous Code

---

### Performance

---

#### Memory-Leaks

<div class="container">
  <div class="col">
  
  <img height=200 src="/img/memory-leaks.jpeg" alt="..."></img>
  
  </div>

  <div class="col">

```kotlin
class LoginActivity : Activity() {

  /* before screen appears */
  override fun onResume() {
    openTheChannel()
  }

  /* before screen be hidden */
  override fun onStop(){
    // close the channel
  }

}
```

---

#### Deep layouts

```xml
<LinearLayout>
  <FrameLayout>
    <ConstraintLayout>
      <View />
      <View />
      <View />
      <View />
    </ConstraintLayout>
  </FrameLayout>
</LinearLayout>
```

---

### Aesthetics

- Names of files, variables, methods, classes...

- File locations...

- Java blood

```kotlin
if (x != null)
  call(x)
```

```kotlin
x?.let { call(x) }
```

---

### Dirt Codes

- Unused imports

- Unused resources like drawables, strings, colors, and so on

- Commented code <small>(I know your pain, don't be afraid, remove that please!)</small>

---

### Accessibility

```xml
<!-- Recommended-->
<ImageView
  android:width="wrap_content"
  android:height="wrap_content"
  contentDescription=
  "This image represents a small dog."/>
```

```xml
  <!--  Don't recommended -->
  <string name="yes">YES</string>
  <!-- Recommended-->
  <string name="yes">yes</string>
```

```xml
  <!--  Don't recommended -->
  <TextView android:textSize="16px" />
  <TextView android:textSize="16dp" />
  <!-- Recommended-->
  <TextView android:textSize="16sp" />
```

---

### Dangerous Code

---

#### Architecture violation

<img src="/img/architecture-violation.png" alt="..."></img>

---

#### Similar components

> Component X does *Y*

> Component Z does *Y*

> Component A does *Y*

---

#### Danger code zones

<small>

The danger code is the code that the reviewer looks at the first moment and says:

> ''This code doesn't make any sense''

or 

> ''Nothing uses this code''


</small>

---

### Conclusion

> A good tip is to have your checklist to make your code reviews better.

---

### Useful Links

- [Code Review on Android Projects - Part 1](https://www.linkedin.com/pulse/code-review-android-projects-part-i-gabriel-bronzatti-moro/)

- [Code Review on Android Projects - Part 2](https://www.linkedin.com/pulse/code-review-android-projects-part-ii-gabriel-bronzatti-moro/)

- [Code Review on Android Projects - Part 3](https://www.linkedin.com/pulse/code-review-android-projects-part-iii-final-gabriel-bronzatti-moro/)