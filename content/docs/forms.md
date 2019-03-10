---
id: forms
title: Forms
permalink: docs/forms.html
prev: lists-and-keys.html
next: lifting-state-up.html
redirect_from:
  - "tips/controlled-input-null-value.html"
  - "docs/forms-zh-CN.html"
---

React ഇൽ form എലമെന്റ് കളുടെ പ്രവർത്തനം ഇവക് ചില  internal state ഉള്ളതിനാൽ  മറ്റ് DOM എലെമെന്റ്കളിൽ നിന്ന് വ്യത്യസ്തമാണ് ..ഉദ്ദാഹരണമായി താഴെ തന്നിരിക്കുന്ന HTML ഇലെ ഫോം യൂസറിൽ  നിന്നും ഒരു പേര് സ്വീകരിക്കുന്നു .

```html
<form>
  <label>
    Name:
    <input type="text" name="name" />
  </label>
  <input type="submit" value="Submit" />
</form>
```

ഈ ഫോം  നു സാധാരണ html  ഫോം ഒരു യൂസർ submit ചെയ്യുമ്പോ പുതിയ പേജ് ലോഡ്  ചെയ്യുന്ന ഡീഫോൾട് സ്വഭാവം ഉണ്ട് .react ഇലും നമുക് വേണമെങ്കിൽ ഈ സ്വഭാവം ഉപയോഗിക്കാം എങ്കിലും ഈ ഫോം സബ്മിഷൻ കൈകാര്യം ചെയ്യാനും യൂസർ എന്റർ ചെയ്ത വിവരങ്ങൾ അക്സസ്സ് ചെയ്യാനും ജാവാസ്ക്രിപ്റ്റ് ഫങ്ക്ഷന് എഴുതുന്നതാകും ഉത്തമം . ഇത് ചെയ്യാൻ സഹായിക്കുന്ന ഒരു ടെക്‌നിക്ക്  ആണ് "controlled  componenets "

## Controlled Components {#controlled-components}

എച്  ടി  എം എല്ലിൽ  `<input>`, `<textarea>`,`<select>പോലുള്ള ഫോം എലെമെന്റുകൾ  അവരുടെ സ്വഭാവം യൂസർ നൽകുന്ന  ഇന്പുട് അനുസരിച്ചാണ് മാറ്റുന്നത് .എന്നാൽ റിയാക്റ്റിൽ  ഓരോ components ന്റെയും സ്വഭാവം സ്റ്റേറ്റ് പ്രോപ്പർട്ടിയിൽ സൂക്ഷിക്കുകയും  [`setState()`](/docs/react-component.html#setstate) എന്നിവ തിനനുസരിച്ച് മാത്രം മാറുകയും ചെയ്യുന്നു 

ഉദ്ദാഹരണത്തിനു ,നമുക്ക്  മുൻപ് കണ്ട പേര് submit  ചെയ്യുന്ന ഉദാഹരണത്തിൽ പേര് ലോഗ് ചെയ്യണമെങ്കിൽ ഫോം നെ controlled component  ആയി എഴുതാം 

```javascript{4,10-12,24}
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

[**Try it on CodePen**](https://codepen.io/gaearon/pen/VmmPgp?editors=0010)

`value ` atribute സെറ്റ് ചെയ്തിരിക്കുന്നതിനാൽ കാണിക്കുന്ന വാല്യൂ എപ്പോളും `this.state.value` ആയിരിക്കും . handleChange `ഓരോ തവണ കീ അമർത്തുമ്പോഴും റൺ ചെയ്യുന്നതിനാൽ react സ്റ്റേറ്റ് ,കാണിക്കുന്ന വില എന്നിവ മാറി കൊണ്ടിരിക്കും 
controlled components  വഴി ഓരോ സ്റ്റേറ്റ് മ്യൂറ്റേഷനും അതുമായി ബന്ധപ്പെട്ട  ഹാൻഡ്‌ലെർ  ഫങ്ക്ഷന് ഉണ്ടാകും .യൂസർ ഇന്പുട് ചെയ്യുമ്പോൾ തന്നെ വാലിഡേറ്റ് ചെയ്യാനും മോഡിഫൈ  ചെയ്യാനും സാധിക്കും.
ഉദ്ദാഹരണത്തിനു  പേരുകൾ വലിയ അക്ഷരത്തിൽ തന്നെ വേണമെങ്കിൽ `handleChange ` ഫങ്ക്ഷന് താഴെ തന്ന പോലെ എഴുതിയാൽ മതിയാകും 
```javascript{2}
handleChange(event) {
  this.setState({value: event.target.value.toUpperCase()});
}
```

## The textarea Tag {#the-textarea-tag}

എച് ടി  എം എല്ലിൽ  ടെക്സ്റ്റ് ഏരിയയുടെ നിർവചനം അതിന്റെ ഓപ്പണിങ് -ക്ലോസിങ് ടാഗുകളുടെ ഇടയിലാണ്  

```html
<textarea>
  Hello there, this is some text in a text area
</textarea>
```

React ൽ അതിനു പകരം `<textarea>` വാല്യൂ ആട്രിബ്യുട്ട ആണ് ഉപയോഗിക്കുന്നത് .ഒറ്റവരി ഇൻപുട്ട് സ്വീകരിക്കുന്ന ഫോം പോലെ തന്നെ നമുക്ക് `<textarea>` വെച്ചുള്ള  ഫോം നിര്മിക്കാവുന്നതാണ്  
```javascript{4-6,12-14,26}
class EssayForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 'Please write an essay about your favorite DOM element.'
    };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('An essay was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Essay:
          <textarea value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

`this.state.value`ഒരു കൺസ്ട്രക്ടർ വെച്ച് ഇനിഷ്യലൈസ് ചെയ്തത് കൊണ്ടാണ് ടെക്സ്റ്റ് ഏരിയ ആദ്യമേ തന്നെ ചില ടെക്സ്റ്റ് കാണിക്കുന്നത് 

## The select Tag {#the-select-tag}

എച്ച് ടി എം എല്ലിൽ  `<select>` ഉപയോഗിച്ചാണ് ഡ്രോപ് ഡൗൺ ലിസ്റ്റ് ഉണ്ടാക്കുന്നത് .ഉദ്ദാഹരണത്തിനു ഈ ഫ്‌ളേവറുകളുടെ ഡ്രോപ്പ് ഡൗൺ ലിസ്റ്റ്  നോക്കുക 

```html
<select>
  <option value="grapefruit">Grapefruit</option>
  <option value="lime">Lime</option>
  <option selected value="coconut">Coconut</option>
  <option value="mango">Mango</option>
</select>
```

Coconut ഓപ്ഷൻ സെലെക്ടഡ് ആയിരിക്കുന്നത് `selected` ആട്രിബ്യുട്ട  കാരണം ആണെന്ന് ശ്രദ്ധിക്കുക .ഇതിനു പകരം react ൽ  സെലക്ട് ന്റെ  റൂട്ടിൽ ഒരു `value` ആട്രിബ്യുട്ട് ഉപയോഗിക്കുകയാണ് ചെയ്യുക .ഒരിടത്ത്  മാത്രം മാറ്റം വരുത്തിയാൽ മതി എന്നത് കൊണ്ട് controlled component ഉപയോഗിക്കുന്നത് ഉപകാരപ്രദമായിരിക്കും .ഉദ്ദാഹരണം 

```javascript{4,10-12,24}
class FlavorForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: 'coconut'};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('Your favorite flavor is: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Pick your favorite flavor:
          <select value={this.state.value} onChange={this.handleChange}>
            <option value="grapefruit">Grapefruit</option>
            <option value="lime">Lime</option>
            <option value="coconut">Coconut</option>
            <option value="mango">Mango</option>
          </select>
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

[**Codepen ൽ ശ്രമിക്കുക **](https://codepen.io/gaearon/pen/JbbEzX?editors=0010)

`<input type="text">`, `<textarea>`,`<select>` എന്നിവ  ഒരേപോലെ പ്രവർത്തിക്കുന്നു അതായത് `value` ആട്രിബ്യുട്ട സ്വീകരിക്കുന്നു .അതുപയോഗിച്ചു controlled components നിര്മിക്കാവുന്നതാണ് .
> Note
>
> 
`value` ആട്രിബ്യുട്ടിലേക്ക്  അറേ പാസ് ചെയ്താൽ സെലെക്ടിൽ  ഒന്നിൽ കൂടുതൽ ഓപ്ഷനുകൾ  തിരഞ്ഞെടുക്കാൻ സാധിക്കും `select` 
>
>```js
><select multiple={true} value={['B', 'C']}>
>```

## The file input Tag {#the-file-input-tag}

എച് ടി എം എല്ലിൽ  [File API](https://developer.mozilla.org/en-US/docs/Web/API/File/Using_files_from_web_applications).ഉപയോഗിച്ച്  ഒന്നോ അനധിലധികമോ ഫയലുകൾ ജാവാസ്ക്രിപ്റ്റ് വഴി സെർവറിലേക്  അപ്‌ലോഡ് ചെയ്യാൻ  `<input type="file">` ടാജ് വഴി സാധിക്കുന്നു
```html
<input type="file" />
```

ഇതിന്റെ വില വായിക്കാൻ മാത്രം സാധിക്കുന്നതായത് കൊണ്ട്  ഇത് React ൽ ഇതൊരു **uncontrolled** component ആണ് . [ഈ ഡോക്യൂമെന്റിൽ  പിന്നീട് ](/docs/uncontrolled-components.html#the-file-input-tag)
## Handling Multiple Inputs {#handling-multiple-inputs}

നിങ്ങൾക് ഒന്നിൽ കൂടുതൽ  കോൺട്രോൾഡ് `input` എലെമെന്റ്സ് കൈകാര്യം ചെയ്യണ്ടി വരുമ്പോ ഓരോ എലെമെന്റിനും  `name`ആട്രിബ്യുട്ട് കൊടുക്കുകയാണെങ്കിൽ  ഹാൻഡ്‌ലെർ  ഫങ്ക്ഷന്  `event.target.name` ന്റെ വില സാനുസരിച് എന്ത്  ചെയ്യണമെന്ന് തീരുമാനിക്കാവുന്നതാണ് .

ഉദാഹരണത്തിന്

```javascript{15,18,28,37}
class Reservation extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isGoing: true,
      numberOfGuests: 2
    };

    this.handleInputChange = this.handleInputChange.bind(this);
  }

  handleInputChange(event) {
    const target = event.target;
    const value = target.type === 'checkbox' ? target.checked : target.value;
    const name = target.name;

    this.setState({
      [name]: value
    });
  }

  render() {
    return (
      <form>
        <label>
          Is going:
          <input
            name="isGoing"
            type="checkbox"
            checked={this.state.isGoing}
            onChange={this.handleInputChange} />
        </label>
        <br />
        <label>
          Number of guests:
          <input
            name="numberOfGuests"
            type="number"
            value={this.state.numberOfGuests}
            onChange={this.handleInputChange} />
        </label>
      </form>
    );
  }
}
```

[**Try it on CodePen**](https://codepen.io/gaearon/pen/wgedvV?editors=0010)

ഇൻപുട്ട് അനുസരിച്ച്  കീ നെയിം മാറ്റാൻ ഇ എസ് 6 [computed property name](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Object_initializer#Computed_property_names)  സിന്റാക്സ് ഉപയോഗിച്ചത് ശ്രദ്ധിക്കുക 
```js{2}
this.setState({
  [name]: value
});
```

ഇത് ഇ എസ  5 ലെ താഴെ തന്ന കോഡ് നു സമാനം ആണ് :

```js{2}
var partialState = {};
partialState[name] = value;
this.setState(partialState);
```

 `setState()` സ്വയം [പാർഷ്യൽ  സ്റ്റേറ്റ് നെ ഇപ്പോളത്തെ സ്റ്റേറ്റ് ആക്കുന്നത് കൊണ്ട് ](/docs/state-and-lifecycle.html#state-updates-are-merged),നമ്മൾ മാറ്റമുള്ള സ്ഥലങ്ങളിൽ മാത്രം ഇതിനെ വിളിച്ചാൽ മതിയാകും 
## Controlled Input Null Value {#controlled-input-null-value}

[controlled component](/docs/forms.html#controlled-components) ന്റെ പ്രോപ് വാല്യൂ പറഞ്ഞു കൊടുത്തിരിക്കുന്നത് കൊണ്ട് യൂസർ ഇന്പുട്ട് അനാവശ്യമായി ,മാറുന്നത് തടയുന്നു .`value` പറഞ്ഞു കൊടുത്താൽ ഇന്പുട്ട്  എഡിറ്റബിൾ  ആയിരിക്കും .അത് അബദ്ധത്തിൽ  `undefined ` ഓ  `null `നോ ആകാനുള്ള സാധ്യത ഉണ്ട് .

താഴെ തന്നിരിക്കുന്ന കോഡ് ഇത് കാണിച്ച തരും  (ഇന്പുട്ട്  ആദ്യം എഡിറ്റബിൾ അല്ല , എന്നാൽ അൽപ്പം കഴിഞ്ഞു  എഡിറ്റബിൾ ആകും )

```javascript
ReactDOM.render(<input value="hi" />, mountNode);

setTimeout(function() {
  ReactDOM.render(<input value={null} />, mountNode);
}, 1000);

```

## Alternatives to Controlled Components {#alternatives-to-controlled-components}

 നിലവിൽ  ഉള്ള കോഡ് ബേസ്  React ലേക്ക് മാറ്റുകയോ ,React നു പുറത്തുള്ള ലൈബ്രററി ഇന്റഗ്രേറ്റ് ചെയ്യുമ്പോളോ , ഒക്കെ കോൺട്രോൾഡ് കോംപോണേന്റ്സ് ഉപയോഗിക്കുമ്പോൾ  എല്ലാ ഡാറ്റ  മാറ്റത്തിനും ഹാൻഡ്‌ലെർ ഫങ്ക്ഷന് എഴുതുന്നത് ഒഴിവാക്കാൻ 
[uncontrolled components](/docs/uncontrolled-components.html),  ഉപയോഗിച്ച്  ഫോം നിര്മിക്കാവുന്നതാണ് 
## Fully-Fledged Solutions {#fully-fledged-solutions}

വാലിഡേഷൻ ,ഫോം സബ്മിഷന് മുതലായവക്ക്  , [Formik](https://jaredpalmer.com/formik)  ജനപ്രിയമായ  ഒരു സൊല്യൂഷൻ ആണ് ..പക്ഷെ ഇത് കോൺട്രോൾഡ്  കംപോണേന്റ്സ്  അടിസ്ഥാനം ആക്കിയാണ് ചെയ്തിരിക്കുന്നത് .അത് കൊണ്ട് അത് പഠിക്കാൻ മറക്കരുതേ 