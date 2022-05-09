---
id: hooks-rules
title: Hooks-ന്റെ നിയമങ്ങൾ
permalink: docs/hooks-rules.html
next: hooks-custom.html
prev: hooks-effect.html
---

React 16.8 ലെ പുതിയതായി ചേർക്കപ്പെട്ട ഫീച്ചർ ആണ് *Hooks*. class എഴുതാതെ state ഉം മറ്റ് React ഫീച്ചറുകളും ഉപയോഗിക്കാനാവും.

Hooks ഒരു JavaScript ഫങ്ഷൻ ആണു, പക്ഷെ അവ ഉപയോഗിക്കുന്നതിനായി 2 നിയമങ്ങൾ ശ്രദ്ധിക്കേണ്ടതുണ്ട്. ഈ നിയമങ്ങൾ പാലിക്കപ്പെടാൻ സഹായിക്കുന്നതിനായി ഞങ്ങൾ [linter plugin](https://www.npmjs.com/package/eslint-plugin-react-hooks) ഉം ഉൾപ്പെടുത്തിയിട്ടുണ്ട്.

### Hooks-നെ ടോപ്പ് ലെവെൽ കമ്പോണന്റിൽ നിന്ന് മാത്രം വിളിക്കുക {#only-call-hooks-at-the-top-level}

<<<<<<< HEAD
**Hooks-നെ ലൂപ്കളിൽ നിന്നോ, കണ്ടീഷനുകളിൽ നിന്നോ Nested ഫങ്ഷനുകളിൽ നിന്നൊ വിളിക്കാൻ പാടുള്ളതല്ല.** പകരം React Hooks എപ്പോഴും ഫങ്ഷന്റെ ടോപ്പ് ലെവലിൽ മാത്രം എഴുതുക. ഇത് വഴി , ഓരോ തവണ കമ്പോണന്റ് റെന്റര്‍ ചെയ്യുമ്പോളും ഒരേ ക്രമത്തിൽ ആണ് വിളിക്കപ്പെടുന്നത് എന്ന് നമുക്ക് ഉറപ്പ് വരുത്താം. അങ്ങനെ React നു ഒന്നിലധികം `useState`നും `useEffect`നും ഫങ്ഷൻ കോളുകളിൽ ഉൾപ്പടെ Hooks ന്റെ അവസ്ഥ ശെരിയായ രീതിയിൽ നിലനിർത്താൻ കഴിയുന്നു. (നിങ്ങൾക്ക് കൂടുതൽ അറിയാൻ താൽപര്യം ഉണ്ടെങ്കിൽ ഞങ്ങൾ ഇതിനെ പറ്റി കൂടുതൽ ഗഹനമായി  [താഴെ](#explanation) പറയുന്നുണ്ട്.)
=======
**Don't call Hooks inside loops, conditions, or nested functions.** Instead, always use Hooks at the top level of your React function, before any early returns. By following this rule, you ensure that Hooks are called in the same order each time a component renders. That's what allows React to correctly preserve the state of Hooks between multiple `useState` and `useEffect` calls. (If you're curious, we'll explain this in depth [below](#explanation).)
>>>>>>> 26a870e1c6e232062b760d37620d85802750e985

### Hooks-നെ React ഫങ്ഷനിൽ നിന്ന് മാത്രം വിളിക്കുക {#only-call-hooks-from-react-functions}

**Hooks-നെ സാധാരണ JavaScript ഫങ്ഷനിൽ നിന്ന് വിളിക്കാൻ പാടുള്ളതല്ല.** പകരം,

* ✅ Hooks-നെ React ഫങ്ഷൻ കമ്പോണന്റിൽ നിന്ന് വിളിക്കാം.
* ✅ നിങ്ങൾ ഇഷ്ടാനുസരണം നിർമ്മിച്ചെടുത്ത Hooks(Custom Hook) ഇൽ നിന്നും വിളിക്കാം (അവയെ കുറിച്ച് നമ്മൾ അടുത്ത [പേജിൽ](/docs/hooks-custom.html) പഠിക്കും ).

ഈ നിയമങ്ങൾ പാലിക്കുക വഴി ഒരു React കമ്പോണന്റിലെ സ്‍റ്റേറ്റ്ഫുൾ ലോജിക് ശെരിയായ രീതിയിൽ തന്നെയാണ് നിങ്ങളുടെ കോഡിലുള്ളതെന്ന് ഉറപ്പിക്കാം.

## ESLint Plugin {#eslint-plugin}

ഈ 2 നിയമങ്ങളും പാലിക്കപ്പെടുന്നു എന്ന് ഉറപ്പ് വരുത്തുന്നതിനായി [`eslint-plugin-react-hooks`](https://www.npmjs.com/package/eslint-plugin-react-hooks) എന്നൊരു പ്ലഗ്ഗിൻ ഞങ്ങൾ പുറത്തിറക്കിയിട്ടുണ്ട്. ഇത് നിങ്ങളുടെ പ്രോജെക്റ്റിൽ ഉൾപ്പെടുത്തി ഉപയോഗിച്ച് നോക്കാവുന്നതാണ്:

This plugin is included by default in [Create React App](/docs/create-a-new-react-app.html#create-react-app).

```bash
npm install eslint-plugin-react-hooks --save-dev
```

```js
// Your ESLint configuration
{
  "plugins": [
    // ...
    "react-hooks"
  ],
  "rules": {
    // ...
    "react-hooks/rules-of-hooks": "error", // Checks rules of Hooks
    "react-hooks/exhaustive-deps": "warn" // Checks effect dependencies
  }
}
```

<<<<<<< HEAD
This plugin is included by default in [Create React App](/docs/create-a-new-react-app.html#create-react-app).

**അടുത്ത പേജിൽ നിങ്ങളുടെ [ഇഷ്ടാനുസരണമുള്ള Hooks](/docs/hooks-custom.html) എങ്ങനെ നിർമ്മിച്ചെടുക്കാം എന്ന് വിശദീകരിക്കുന്നുണ്ട്.** ഈ പേജിൽ ഈ 2 നിയമങ്ങൾ പിന്തുടരേണ്ടതിന്റെ ആവശ്യകത വിശദീകരിക്കുന്നതാണ്.
=======
**You can skip to the next page explaining how to write [your own Hooks](/docs/hooks-custom.html) now.** On this page, we'll continue by explaining the reasoning behind these rules.
>>>>>>> bc91fe4101420f98454a59ac34c1cf1d4d4f4476

## വിശദീകരണം {#explanation}


നേരത്തെ നമ്മൾ [പഠിച്ചത്](/docs/hooks-state.html#tip-using-multiple-state-variables) പോലെ ഒരു കമ്പോണന്റിൽ ഒന്നിലധികം state ഉം effects ഉം ഉപയോഗിക്കാൻ സാധിക്കുന്നതാണ്:

```js
function Form() {
  // 1. Use the name state variable
  const [name, setName] = useState('Mary');

  // 2. Use an effect for persisting the form
  useEffect(function persistForm() {
    localStorage.setItem('formData', name);
  });

  // 3. Use the surname state variable
  const [surname, setSurname] = useState('Poppins');

  // 4. Use an effect for updating the title
  useEffect(function updateTitle() {
    document.title = name + ' ' + surname;
  });

  // ...
}
```

`useState` കോളുകളും അതിന്റെ അനുബന്ധമായ state ഉം React എങ്ങനെ മനസ്സിലാക്കും ? ഉത്തരം ഇതാണ് , **Hooks വിളിക്കപ്പെടുന്നതിന്റെ ക്രമത്തിന്റെ അടിസ്ഥാനത്തിലാണ്**. എല്ലാ റെന്ററുകളിലും Hook-കളെ വിളിക്കുന്നത് ഒരേ ക്രമത്തിൽ ആയതിനാൽ നമ്മുടെ  ഉദാഹരണ പ്രോഗ്രാം ശെരിയായി പ്രവർത്തിക്കുന്നു :

```js
// ------------
// First render
// ------------
useState('Mary')           // 1. Initialize the name state variable with 'Mary'
useEffect(persistForm)     // 2. Add an effect for persisting the form
useState('Poppins')        // 3. Initialize the surname state variable with 'Poppins'
useEffect(updateTitle)     // 4. Add an effect for updating the title

// -------------
// Second render
// -------------
useState('Mary')           // 1. Read the name state variable (argument is ignored)
useEffect(persistForm)     // 2. Replace the effect for persisting the form
useState('Poppins')        // 3. Read the surname state variable (argument is ignored)
useEffect(updateTitle)     // 4. Replace the effect for updating the title

// ...
```

എല്ലാ റെന്ററുകളിലും Hooks വിളിക്കപ്പെടുന്നത് ഒരേ ക്രമത്തിൽ ആയിരിക്കുന്നിടത്തോളം, React നു ശെരിയായ രീതിയിൽ state കളെ അനുബന്ധിക്കാൻ കഴിയുന്നു.മറിച്ച് ഒരു കണ്ടീഷനു അകത്തു നിന്ന് Hook-നെ വിളിച്ചാലോ (ഉദാഹരണമായി `persistForm` എഫെക്റ്റ്  ) ?  

```js
  // 🔴 We're breaking the first rule by using a Hook in a condition
  if (name !== '') {
    useEffect(function persistForm() {
      localStorage.setItem('formData', name);
    });
  }
```

ആദ്യത്തെ റെന്ററിൽ `name !== ''` കണ്ടീഷൻ `true` ആണ്, ഫലമായി Hook റൺ ആയി. യൂസർ, ഫോം ക്ലിയർ ചെയ്താൽ അടുത്ത റെന്ററിൽ കണ്ടീഷൻ `false` ആയിരിക്കും , ഫലമായി ആ Hook വർക്ക് ചെയ്യാതിരിക്കുന്നു. അങ്ങനെ Hook-നെ വിളിക്കുന്ന ക്രമം വ്യത്യസ്തമാകുന്നു:

```js
useState('Mary')           // 1. Read the name state variable (argument is ignored)
// useEffect(persistForm)  // 🔴 This Hook was skipped!
useState('Poppins')        // 🔴 2 (but was 3). Fail to read the surname state variable
useEffect(updateTitle)     // 🔴 3 (but was 4). Fail to replace the effect
```

ഇപ്പോൾ രണ്ടാമത്തെ `useState` കോളിന് എന്താണ് റിട്ടേൺ നൽകേണ്ടത് എന്ന് React നു അറിയില്ല. React കരുതുന്നത്, രണ്ടാമത് വിളിക്കുന്നത് `persistForm` നോട് അനുബന്ധമായ state ആണെന്നാണ്, ഇതിനു മുമ്പുള്ള റെന്ററിൽ സംഭവിച്ചത് പോലെ. പക്ഷെ അതല്ല സംഭവിക്കുന്നത്. പിന്നീടങ്ങോട്ട് റൺ ചെയ്യാതെ പോയ Hook-നു ശേഷമുള്ള Hook-കൾ വിളിക്കപ്പെടുന്നു, തൽഫലമായി ബഗുകൾ ഉണ്ടാകുന്നു.

**അത്കൊണ്ട് Hook-നെ എപ്പോഴും കമ്പോണന്റിന്റെ ടോപ്പ് ലെവലിൽ നിന്ന് മാത്രം വിളിക്കുക.** ഒരു കണ്ടീഷനെ അടിസ്ഥാനമാക്കി Hook വിളിക്കപ്പെടണം എങ്കിൽ , Hook-ന്റെ അകത്ത് കണ്ടീഷൻ നൽകാവുന്നതാണ്:

```js
  useEffect(function persistForm() {
    // 👍 We're not breaking the first rule anymore
    if (name !== '') {
      localStorage.setItem('formData', name);
    }
  });
```

**[ഈ ലിൻറ്റ് റൂൾ](https://www.npmjs.com/package/eslint-plugin-react-hooks) ഉപയോക്കുവനെങ്കിൽ ഈ പ്രെഷ്നത്തേ കുറിച്ച് ആശങ്കപ്പെടേണ്ടതില്ല**. *എന്ത്കൊണ്ട്* Hooks ഇങ്ങനെ പ്രവർത്തിക്കുന്നു എന്നും ഏതൊക്കെ പ്രശ്നങ്ങളെയാണ് ഈ നിയമങ്ങൾ ശെരിയായി നേരിടുന്നത് എന്നും മനസ്സിലായല്ലോ.

## അടുത്ത ഘട്ടങ്ങൾ {#next-steps}

ഇനി നമുക്ക് [Custom Hook](/docs/hooks-custom.html)! എഴുതാൻ പഠിക്കാവുന്നതണ്. Custom Hook-ഇൽ React ന്റെ തനത് Hook-കൾ ഉപയോഗിക്കാവുന്നതാണ്, ഈ കസ്റ്റം Hook വിവിധ കമ്പോണന്റുകളിൽ ഉപയോഗപ്പെടുത്തവുന്നതുമണ്.
