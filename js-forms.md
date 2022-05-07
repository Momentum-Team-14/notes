# Forms and Client-side Validation

---

# Form element, controls, and inputs

- `<form>` (HTMLFormElement)
- `<label>`
- `<input type="...">`
- `<textarea>`
- `<select>` and `<option>`
- `<button>`

---

```html
<form method="post" action="/" id="login-form">
  <div class="input-field">
    <label for="email-input">Email</label>
    <input
      type="email"
      name="email-input"
      id="email-input"
      placeholder="example@domain.com"
      required
    />
  </div>
  <div class="input-field">
    <label for="password-input">Password</label>
    <input type="password" name="password-input" id="password-input" required />
  </div>
  <div class="input-field">
    <input type="submit" value="Log In" />
  </div>
</form>
```

---

# input types

- `text`: the one you use everywhere
- `checkbox`: a checkbox that can be `checked`
- `hidden`: holds data, doesn't appear
- `password`: doesn't show the input
- `radio`: allows a single value to be selected out of multiple choices
- `submit`: button that submits the form
- `reset`: button that clears the form
- `button`: a button with no default behavior

---

# input types, bonus round

- `color`
- `date`
- `datetime-local`
- `email`
- `number`
- `tel`
- `time`
- `url`

##### [MDN Form Input Types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)

---

# Form Events

- `focus`: element gained focus
- `blur`: element lost focus
- `input`: element's value changed
- `change`: "a change to the element's value is committed by the user," usually after losing focus
- `submit`: submit button was pressed
- `reset`: reset button was pressed

---

# Events

- `event.target`
- `event.preventDefault()`

### [MDN Event Reference](https://developer.mozilla.org/en-US/docs/Web/API/Event)

---

# DOM Manipulation, revisited

- `createElement`
- `appendChild`
- `setAttribute`
- `getAttribute`
- `removeAttribute`

---

# Get the value of a form field with `.value`


```html
<input type="email" id="email-input" placeholder="example@gmail.com"/>
```

An input element's `value` property lets you get or set the information it contains:

```js
let email = document.querySelector("#email-input).value

function clearTextField(inputId) {
  document.getElementById(inputId).value = ''
}
```

---

# Form Validation

_Validation_ refers to the process of checking to make sure that data entered by a user is present and correct before it is used programmatically or stored somewhere.

We can validate data on the _client-side_ AND/OR on the _server-side_ (usually both).

If data is _invalid_, we want to know so that we can do something, like generate an error that alerts the user (or not do something! We wouldn't want to save faulty data to a database).
