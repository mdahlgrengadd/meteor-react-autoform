# Meteor-React-Autoform
- [Text](#element-text)
- [Textarea](#element-textarea)
- [Number](#element-number)
- [Date](#element-date)
- [Tickbox](#element-tickbox)
- [Select Dropdown](#element-selectdropdown)
- [Radio Button](#element-radiobuton)

## WARNING
This is still in development. Basic elements are available, more to come soon.

## Basic Usage


### Example
```
  import React from 'react';
  import ReactAutoForm from 'meteor-react-autoform';

  const ContactUsPage = () => (
    <div>
      <h1>Contact Us</h1>
      <ReactAutoForm schema={HelpDesk.simpleSchema} />
    </div>
  );

  export default ContactUsPage;
```

### Parameters
You may pass through the following parameters to control the form build:
 - `useFields={['name', 'text']}` Only the fields `name` and `text` will be in the built form.


### Elements
#### Global paramters
 - `label` String | Input label
 - `max` Number | Set the max length of an input
```
  description: {
    type: String,
    label: 'Description',
    max: 10
  }
```

#### Text <a name="element-text"></a>
A normal text input will only need a type of `String` to display. See [Material-UI text field](http://www.material-ui.com/#/components/text-field) to find what properties are available for passing into our `materialForm` object.
```
  description: {
    type: String,
    materialForm: {
      hintText: 'Please enter the description...'
    }
 }
```
```
  password: {
    type: String,
    label: 'Password',
    materialForm: {
      type: 'password'
    }
  }
```

#### Textarea <a name="element-textarea"></a>
Inside the `materialForm` object, using either `materialForm.rows` `materialForm.rowsMax` or `materialForm.multiLine` will cause the input to turn into a textarea. See [Material-UI text field](http://www.material-ui.com/#/components/text-field) to find what properties are available for passing into our `materialForm` object.
```
  description: {
    type: String,
    materialForm: {
      rows: 1,
      rowsMax: 3,
      multiLine: true
    }
  }
```

#### Number <a name="element-number"></a>
Type `Number` will change the element to a number input. `min` and `max` values are taken into consideration if available. See [Material-UI text field](http://www.material-ui.com/#/components/text-field) to find what properties are available for passing into our `materialForm` object.
```
  favoritePositiveInteger: {
    type: Number,
    max: 10,
    min: 5,
    materialForm: {
      step: 0.2
    }
  }
```


#### Date <a name="element-date"></a>
Type `Date` will provide a date select. `min` and `max` values are taken into consideration if available. See [Material-UI date picker](http://www.material-ui.com/#/components/date-picker) to find what properties are available for passing into our `materialForm` object.
```
  birthday: {
    type: Date,
    label: 'Your birthday',
    //min: new Date('2014-01-01T00:00:00.000Z'),
    materialForm: {
      value: new Date('2014-10-18T00:00:00.000Z'),
      dateMode: 'landscape'
    }
  }
```

#### Tick box <a name="element-tickbox"></a>
Type `Boolean` will use `materialForm.switcher` to determine to display either a checkbox or a toggle component. By default will use the [checkbox Material-UI component](http://www.material-ui.com/#/components/checkbox) `materialForm.switcher = 'Checkbox'`, or if you can change it to use the [toggle component](http://www.material-ui.com/#/components/toggle) `materialForm.switcher = 'Toggle'`. Check out the respective Material-UI documentation on each component to find out what other properties are available for passing into our `materialForm` object.
```
  agree: {
    type: Boolean,
    label: 'Do you agree?',
    materialForm: {
      switcher: 'Checkbox'
      // OR
      //switcher: 'Toggle'
    }
  }
```

#### Select dropdown menu <a name="element-selectdropdown"></a>
Use `allowedValues = []` to create a select dropdown menu. You can provide `materialForm.options = []` to pass through an object`[label: 'Example', value: 'durp']` for each option. You can pass through any [select-field properties](http://www.material-ui.com/#/components/select-field) by using `materialForm.selectOptions = []`.
```
  choose3: {
    type: Number,
    allowedValues: [
      1,
      2,
      3
    ],
    optional: true,
    label: 'Choose a number',
    materialForm: {
      selectOptions: {
        className: 'selectExample'
      },
      options: [
        {
          label: 'One',
          value: 1
        },
        {
          label: 'Two',
          value: 2
        },
        {
          label: 'Three',
          value: 3
        }
      ]
    }
  }
```

#### Radio button <a name="element-radiobuton"></a>
When you use `allowedValues = []` with `materialForm.switcher = 'Radio'` this will display radio box options. You can provide `materialForm.options = []` and pass through any [RadioButton properties](http://www.material-ui.com/#/components/radio-button) into each option, you can also pass through [RadioButtonGroup properties](http://www.material-ui.com/#/components/radio-button) by using `materialForm.groupOptions = []`.
```
  agree: {
    type: String,
    allowedValues: [
      'red',
      'green'
    ],
    label: 'What colour is the sky?',
    materialForm: {
      switcher: 'Radio',
      groupOptions: {
        className: 'radioExample'
      },
      options: [
        {
          label: 'Red',
          value: 'red'
        },
        {
          label: 'Green',
          value: 'green'
        }
      ]
    }
  }
```

# Credits
Developed and maintained by [Aluminati](http://www.aluminati.net/)