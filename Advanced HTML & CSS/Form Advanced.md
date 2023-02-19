
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


