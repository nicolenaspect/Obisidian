
## Do's and dont's

1. The best place to show validation errors - near inputs. Don't gather all of them in one place.  ![[Pasted image 20230219145600.jpg]]

2. Don't disable the submit button. Allow users to click on it and see the validation errors. Users might scroll past some of the inputs without filling them. If the submit button is blocked, then they won't know what to do next.![[Pasted image 20230219145646.jpg]]

3. Consider providing positive feedback as well as negative.![[Pasted image 20230219145732.jpg]]

   4. Use human language, not a technical one ![[Pasted image 20230219145900.jpg]]


  5. If you put an exclamation icon next to inputs it might help colorblind people to notice the error.![[Pasted image 20230219145941.jpg]]

 6. Don't hide error messages under icons.![[Pasted image 20230219150004.jpg]]

7.  Show password rules right away.![[Pasted image 20230219150019.jpg]]

8. Help users to avoid mistakes.![[Pasted image 20230219150107.jpg]]

## Validation Behaviors

- ! Aggressive mode: Triggered when the user presses a key.  Poor UX, because the user might not have finished inputting his data but the error is already thrown.
- ! Lazy mode: Triggered when the user leaves the input. Looks better, but it triggered ONLY when the user leaves the input. If he made a mistake, and then returned back to the input and fixed it, it'll still be red until he leaves the input.
- ! Passive mode: Triggered when the form is submitted. Poor UX, especially for big forms. Imagine the user filled 10 inputs with incorrect data and you throw 10 errors at once...
- $ Eager mode: a combination of aggressive and lazy. It first validates when the user leaves the input, then if the input is invalid it will behave aggressively until the input is valid again and it will go back to being lazy. - https://twitter.com/vponamariov/status/1380182270808633345 