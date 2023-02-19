
## Required Validation

We will often want to ensure specific fields have been filled in before submitting the form, for example, the email and password in a login form.

To make a field required, we simply add the `required` attribute to it:

``` html
<form action="#" method="get">
  <div>
    <label for="user_email">*Email:</label>
    <input type="email" id="user_email" name="user_email" required>
  </div>
  <br>

  <div>
    <label for="user_password">*Password:</label>
    <input type="password" id="user_password" name="user_password" required>
  </div>

  <button type="submit">Login</button>
</form>
```

To ensure a good user experience and to meet accessibility guidelines, we should always indicate which fields are required. This will often be done by adding an asterisk(*) to the required field label like we have done in the example.

## Text Length Validations

Минимално или максимално количество текст в дадено поле, например 140 знака в туитър.

### Minimum Length Validation

Задаваме  `minlength` атрибут
 
``` html
<form action="#" method="get">
  <div>
    <textarea placeholder="What's happening?" minlength="3"></textarea>
  </div>
  
  <button type="submit">Tweet</button>
</form>
```

### Maximum Length Validation

Задаваме `maxlength` атрибут 

``` html
<form action="#" method="get">
  <div>
    <textarea placeholder="What's happening?" maxlength="20"></textarea>
  </div>

  <button type="submit">Tweet</button>
</form>
```


### Combining Validation


``` html
<form action="#" method="get">
  <div>
    <textarea placeholder="What's happening?" minlength="5" maxlength="20"></textarea>
  </div>
  
  <button type="submit">Tweet</button>
</form>
```

## Number Range Validation 

Just like we often need to control the length of text-based form controls, there will be many situations where we will want to control the range of values users can enter into number based form controls.

We can do this with the min and max attributes, which allows us to set the lower and upper bounds of the value entered into the form control. The min and max attributes only work with number-based form controls such as the number, dates and time inputs. You can view the complete list of supported elements on [MDN’s documentation](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/max#syntax).

Some real-world use cases for using these validations would be limiting the quantity on a product order form or choosing the number of passengers on a flight booking form.

### Min Validation

To add a minimum value validation, we give the form control a `min` attribute with an integer value which represents the minimum number we want the form control to accept:

``` html
<form action="#" method="get">
  <div>
    <label for="quantity">Quantity</label>
  </div>
  <input type="number" id="quantity" name="quantity" min="1" value="0">
  
  <div>
    <button type="submit">Place Order</button>
  </div>
</form>
```

### Max Validation

To add a maximum value validation, we give the form control a `max` attribute with an integer value which represents the maximum number we want the form control to accept:

``` html
<form action="#" method="get">
  <div>
    <label for="passengers">Passengers</label>
  </div>
  <input type="number" id="passengers" name="passengers" max="5" value="0">
   
  <div>
    <button type="submit">Book</button>
  </div>
</form>
```

## Pattern Validations

To ensure we get the correct information from users, we will often want to ensure data matches a particular pattern. Real-world applications would be checking if a credit card number or a zipcode is in the correct format.

To add a pattern validation, we give the form control a `pattern` attribute with a [regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) as the value. In our example we are using the pattern validation to ensure a US zip code is in the correct format (5 numbers followed by an optional dash and 4 more numbers:

``` html
<form action="#" method="get">
  <div>
    <label for="zip_code">Postal / Zip Code:</label>
  </div>

  <input type="text" id="zip_code" name="zip_code" pattern="(\d{5}([\-]\d{4})?)" required>

  <div>
    <button type="submit">Submit</button>
  </div>
</form>
```

## Styling Validations

We can target form controls that have passed or failed validations using the `:valid` and `:invalid` pseudo-classes.