# hof-util-countries

A utility to parse `homeoffice-countries` into a usable format for hof select elements

By default hof select elements expect a list of options as an objet with `value` and `label` properties. If passed an array of strings as options it will attempt to translate the strings with some field-specific keys attached.

## Usage

In field configuration:

```js
{
  country: {
    mixin: 'select',
    validate: 'required',
    options: require('hof-util-countries')()
  }
}
```

## Options

If needed, the following options can be passed into the countries function:

* `filter` - `Function` - applies a filter to the list of country names before mapping them
* `parse` - `Function` - applies a transform to the country name before setting the label

## i18n

If you wish to translate the countries into outher languages, you may want the labels to be in the form of translation keys. In this case you can use a `parse` option to convert the country names into a translation key:

```js
const countries = require('hof-util-countries');
const options = countries({
  parse: country => `countries.${country.toLowerCase().split(' ').join('-')}`
});
```

You can then define a single translation for country names to be used for all country list instances.
