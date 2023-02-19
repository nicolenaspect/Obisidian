
## Placeholder


- ! **Caution**  Never misuse the `placeholder` attribute as a label. The placeholder is meant for giving a hint about the type of data you should enter, not for describing a form control. Learn more about why you should consider [avoiding placeholders](https://www.smashingmagazine.com/2018/06/placeholder-attribute/).


- `placeholder` не се превежда от браузърите, което може да обърка потребителя 
- Риск за проблеми с контраста 
- Може да скрие важна информация, когато потребителят въвежда данни
- При използване вместо `label`, блокира асистиращите технологии
- Лимитирани стилови опции
- Може да изглежда като вече въведени данни и да бъде пропусната

Възможна алтернатива е прилагането на `placeholder` съдържанието върху `input` полето, под `label`

![[solution.webp]]

```html
<div class="input-wrapper">
  <label for="employee-id">
    Your employee ID number
  </label>
  <p
    id="employee-id-hint"
    class="input-hint">
    Can be found on your employee intranet profile. Example: <samp>a1234567-89</samp>.
  </p>
  <input
    id="employee-id"
    aria-describedby="employee-id-hint"
    name="id-number"
    type="text" />
</div>
```

## Buttons

- Препоръчителният размер на бутон е поне 48px (tap target)

## Internationalization and localization

The first step to make your site localization-ready is to define the language attribute `lang` on the `<html>` element. This attribute enables screen readers to invoke the correct pronunciation, and helps browsers offer a translation of the page if the defined language is not the default browser language.

```html
<html lang="en-us">
```

Say you translated a form to German. How can you make sure search engines and browsers know about the translated version? You can add `<link>` elements in your site's `<head>` describing the alternate versions.

```html
<link rel="alternate" title="The form element"  href="https://example.com/en/form" hreflang="en"><link rel="alternate" title="Das Formularelement"  href="https://example.com/de/form" hreflang="de">
```

You can't translate your form into every language, but you can ensure translation tools can translate it for you.

To ensure translation tools translate all the text on your form, make sure all text is defined in HTML and is visible. Some tools also work with content defined in JavaScript, but to improve compatibility, try to include as much text as possible in HTML.

- & Avoid using the `aria-label` attribute to describe elements. Many translation tools aren't able to translate the `aria-label` attribute. Learn more why `aria-label`[doesn't translate](https://adrianroselli.com/2019/11/aria-label-does-not-translate.html).

Different languages use different writing systems and character sets. Some scripts are written from left to right, and some from right to left.

To ensure your form works for different writing systems, you can use [CSS logical properties](https://developer.mozilla.org/docs/Web/CSS/CSS_Logical_Properties).

### Name Formats

If you have a name with [non-Latin characters](https://web.dev/payment-and-address-form-best-practices/#unicode-matching), you may have encountered the issue that your name is reported as `invalid` in some forms. When you build forms, make sure to allow all possible characters—and do not assume that a name only consists of Latin characters.

### Address Formats


The headquarters of Google is at 1600 Amphitheatre Parkway, Mountain View, CA 94043, United States.

This address includes the street number, street, city, state, postal code, and country. In your country, the address format may be totally different. How can you ensure everybody can enter their address in your form?

One way is to use generic inputs.
Learn more about other ways to work with [international address fields](https://www.uxmatters.com/mt/archives/2008/06/international-address-fields-in-web-forms.php).


## Security and privacy

- & A secure form means that all data is encrypted, kept secure, and no unauthorized access can happen. To ensure privacy, only save the data you need, only save personal data after consent, ensure the user is in full control of their data, and never share user data with others without the user's consent.

- Request as little data as possible, don't ask for data you don't need

- [Always use HTTPS](https://web.dev/secure/#secure-connections-with-https), especially for pages that include a form. With HTTPS, data is encrypted when coming from the server and when going back to the server. Say you're sitting in a café using public Wi-Fi. You open an e-commerce site and fill in your credit card information to purchase something. If the website uses HTTP, anyone (with the skills to do so) on the same public Wi-Fi could see your credit card information. If the website uses HTTPS, the data is encrypted and therefore protected from anyone trying to access it. On your site, you should also make sure to redirect any HTTP requests to HTTPS. Learn more about [how to redirect all traffic to HTTPS](https://geekflare.com/http-to-https-redirection/).

- Use `POST` requests for every form where data that's personal or otherwise sensitive may be submitted. This way, the data is only visible to the backend script processing it.

- use `localStorage` to store personal data in the browser.

- Ensure users can safely sign up and sign in  - User account [authentication](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) is a complex issue in terms of privacy and security. It may be better to use a [third-party identity provider](https://web.dev/sign-up-form-best-practices/#federated-login), instead of building your own secure authentication system.

- Help users access their personal data - Every website available in the European Union (EU) has to follow [General Data Protection Regulation](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) (GDPR), even if the site is not based in the EU. GDPR sets guidelines for the collection and processing of personal information from people living in the EU. Consent is required to process personal data, users can request personal information that you store at any time, and you have to officially announce data leaks. A good thing for the user, as this helps to ensure that their privacy is respected. Learn more about [GDPR](https://www.smashingmagazine.com/2018/02/gdpr-for-web-developers/). Make sure your users know how you plan to process personal data. Transparency is the key to trust. Users should always be able to access, modify, and delete all data you saved for them.
- 
- Ensure users can update their personal data - Make it easy for users to update their personal data, including passwords, email addresses, and usernames. Notify users about changes to their stored personal data, and ensure users can revoke changes. For example, send an email to the previous and new email address after users change their email address. 

- ==Separate the concept of user account and user identity to simplify implementing third-party identity provision. Allow users to change their username and link multiple identities to a single user account, for example if they sign up with an email and password, then sign up with a third-party identity provider.== 

- Make it easy for users to delete their account, including all associated data, and where relevant, make it possible to download data. Account deletion is a [legal requirement](https://ec.europa.eu/info/law/law-topic/data-protection_en) in some regions. ==Link to your privacy policy on each page with a form, especially if personal data is processed. ==

- Require an additional authentication step, for example, re-entering the current password, to view or change personal information on your site. Find out more: [Web Application Privacy Best Practices](https://www.w3.org/TR/app-privacy-bp/).

- Validate the data on the   