---
id: hooks-intro
title: Hooks പരിചയപ്പെടുത്തുന്നു
permalink: docs/hooks-intro.html
next: hooks-overview.html
---

React 16.8 ലെ പുതിയതായി ചേർക്കപ്പെട്ട ഫീച്ചർ ആണ് *Hooks*. class എഴുതാതെ state ഉം മറ്റ് റീയാക്റ്റ് ഫീച്ചറുകളും ഉപയോഗിക്കാനാവും.

```js{4,5}
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

`useState` എന്ന ഈ ഫങ്ക്ഷന് ആണ് നമ്മൾ കാണുന്ന ആദ്യത്തെ Hook. നിങ്ങൾക്കു ഇപ്പോൾ ഈ ഉദാഹരണം മുഴുവൻ ആയി മനസിലാക്കണം എന്നില്ല! നമുക്കു അതിനായി വരുന്ന പേജുകളിൽ കൂടുതൽ പഠിക്കാം.

**[അടുത്ത പേജിൽ](/docs/hooks-overview.html) നിങ്ങൾക്കു Hooks പഠിച്ചു തുടങ്ങാം.** ഈ പേജിൽ എന്ത് കൊണ്ട് ആണ് Hooks ചേർക്കുന്നത് എന്നതിന്റെ വിശദീകരണവും, എങ്ങനെ അവ നല്ല അപ്പ്ലികേഷൻസ് എഴുതാൻ സഹായിക്കും എന്നും കാണാം.

>കുറിപ്പ്
>
<<<<<<< HEAD
>React 16.8.0 ൽ ആണ് hooks ലൈബ്രറിയിൽ ചേർക്കുന്നത്. നിങ്ങൾ hooks ഉപയോഗിക്കുമ്പോൾ React DOM ഉൾപ്പടെ എല്ലാ ലൈബ്രറികളും അപ്ഗ്രേഡ് ചെയാൻ മറക്കരുത്. React Native [the 0.59 release of React Native](https://facebook.github.io/react-native/blog/2019/03/12/releasing-react-native-059) വേര്‍ഷന്‍ മുതല്‍ മുതൽ hooks സപ്പോര്‍ട്ട് ചെയ്യുന്നുണ്ട്. 
=======
>React 16.8.0 is the first release to support Hooks. When upgrading, don't forget to update all packages, including React DOM.
<<<<<<< HEAD
>React Native supports Hooks since [the 0.59 release of React Native](https://reactnative.dev/blog/2019/03/12/releasing-react-native-059).
>>>>>>> bc91fe4101420f98454a59ac34c1cf1d4d4f4476
=======
>React Native has supported Hooks since [the 0.59 release of React Native](https://reactnative.dev/blog/2019/03/12/releasing-react-native-059).
>>>>>>> 38bf76a4a7bec6072d086ce8efdeef9ebb7af227

## ദൃശ്യം {#video-introduction}

React Conference 2018 ൽ വച്ച് സോഫി അൽപ്പർട്ടും ഡാൻ അബ്രമോവും കൂടി ആണ് hooks ആദ്യം ആയി അവതരിപ്പിച്ചത്. പിന്നീട് റയാൻ ഫ്ലോറെൻസ് hooks ഉപയോഗിച്ച് ഒരു അപ്ലിക്കേഷൻ എഴുതി കാണിക്കുകയും ചെയ്തു. അതിന്റെ ദൃശ്യങ്ങൾ ചുവടെ ചേർക്കുന്നു.
=======
<iframe width="650" height="366" src="//www.youtube.com/embed/dpw9EHDh2bM" frameborder="0" allowfullscreen></iframe>

## ബ്രേക്കിംഗ് മാറ്റങ്ങൾ ഇല്ല {#no-breaking-changes}

മുൻപോട്ടു പോകുന്നതിനു മുൻപ് അറിഞ്ഞിരിക്കേണ്ട കുറച്ചു കാര്യങ്ങൾ:

* **Completely opt-in.** ഇപ്പോൾ നിങ്ങൾ എഴുതിയിട്ടുള്ള components ഒന്നും മാറ്റാതെ തന്നേ നിങ്ങൾക്കു Hooks ഉപയോഗിച്ചു കോഡ് ചെയ്തു തുടങ്ങാവുന്നത് ആണ്. ഇപ്പോൾ പഠിക്കേണ്ട എന്ന് തോന്നുന്നുണ്ടെങ്കിൽ വേണ്ട എന്ന് വക്കാം.
* **100% backwards-compatible.**  ഇപ്പോൾ ഉള്ള code നെ പൊട്ടിക്കുന്ന മാറ്റങ്ങൾ ഒന്നും hooks കൊണ്ട് വരുന്നില്ല.
* **ഇപ്പോൾ ലഭ്യമാണ്** React 16.8.0 മുതൽ hooks ലഭ്യം ആണ്.

**class React ൽ നിന്നും ഒഴിവാകുകയല്ല.** ക്രമേണ എങ്ങനെ hooks ഉപയോഗിച്ചു തുടങ്ങാം എന്ന് [ചുവടെ](#gradual-adoption-strategy) ചേർക്കുന്നു.

**Hooks നിങ്ങളുടെ React അറിവുകൾക്ക് പകരം വെക്കാവുന്ന ആകുന്ന ഒന്നല്ല** നിങ്ങൾക്കു ഇതിനോടകം അറിയാവുന്ന React കൺസെപ്റ്സ് ഉപയോഗിക്കാൻ ഉള്ള ഒരു പുതിയ മാർഗം മാത്രം ആണ്: props, state, context, refs, and lifecycle. ഇവയെ സംയോജിപ്പിക്കാൻ ഉള്ള പുതിയ മാർഗങ്ങൾ നമ്മൾ പിന്നീട് കാണും.

**നിങ്ങൾക്കു hooks പഠിക്കാൻ തിരക്കു ആയെങ്കിൽ [അടുത്ത പേജിലേക്ക്](/docs/hooks-overview.html) കടക്കാം.** ഞങ്ങൾ എന്ത് കൊണ്ട് ആണ് hooks അവതരിപ്പിക്കുന്നത് എന്നും, എങ്ങനെ അവ ഉപയോഗിക്കാൻ ആസൂത്രണം ചെയുന്നു എന്നും അറിയാൻ തുടർന്ന് ഈ പേജ് വായിക്കാം.

## പ്രചോദനം {#motivation}

ഫേസ്ബുക്കിൽ അഞ്ചു വര്ഷം ആയി എഴുതി വരുന്ന പത്തു പതിനായിരം Components ൽ കണ്ടു വരുന്ന കുറച്ചു പ്രശ്നങ്ങളുടെ ഒരു പരിഹാരം ആണ് Hooks എന്നതിൽ എത്തി നില്കുന്നത്. നിങ്ങൾ React ന്റെ ഒരു വിദ്യാർഥിയോ, സ്ഥിരം ഉപഭോക്താവോ, മറ്റൊരു ലൈബ്രറി കൂടുതൽ ഇഷ്ടപെടുന്ന ഒരാളോ, ആരും ആവട്ടെ, ഇവിടെ പറയുന്ന പ്രശ്നങ്ങൾ നിങ്ങൾക്കു തിരിച്ചറിയാൻ കഴിയും.

### Components തമ്മിൽ ലോജിക് പുനരുപയോഗിക്കാൻ ഉള്ള ബുദ്ധിമുട്ട് {#its-hard-to-reuse-stateful-logic-between-components}

ഇത് വരെ React ൽ Components ലെക് പുനരുപയോഗിക്കാവുന്ന ലോജിക് ബന്ധിപ്പിക്കാൻ ഉള്ള മാർഗം ഉണ്ടായിരുന്നില്ല. [റെൻഡർ props](/docs/render-props.html) അല്ലെങ്കിൽ [Higher Order Components](/docs/higher-order-components.html) പോലുള്ള മാതൃകകൾ നിങ്ങൾ നേരത്തെ ശ്രദ്ധിച്ചു കാണും. പക്ഷെ ഇവ ഉപയോഗിക്കുമ്പോൾ Components പുനർരൂപീകരിക്കേണ്ടി വരും എന്നത് മുഖ്യമായ ഒരു പോരായ്മ ആയിരുന്നു. ഇത് കൂടാതെ, ഇവ "Wrapper Hell" എന്ന് വിശേഷിപ്പിക്കാവുന്ന ഒരു പ്രതിഭാസം കൂടി ഒപ്പം കൊണ്ട് വന്നു. റെൻഡർ Props,Higher Order Components എന്നിവ ഉപയോഗിക്കുമ്പോൾ React Dev Tools ൽ നിങ്ങൾക്കു കാണാൻ ആകുന്നത് DOM എലെമെന്റ്സിന് ഒപ്പം കുറെ  പുറംചട്ടകൾ കൂടി വരുന്നത്. ഇത് debugging അനുഭവം ബുദ്ധിമുട്ടേറിയതു ആക്കി. ഈ പുറം ചട്ടകളെ [ഫിൽറ്റർ ചെയ്തു മാറ്റാൻ വഴികൾ](https://github.com/facebook/react-devtools/pull/503) ഉണ്ടെങ്കിലും, പ്രശ്നം വ്യക്തം ആയിരുന്നു: ലോജിക് ആയോജിപ്പിക്കാൻ React ൽ മെച്ചപ്പെട്ട പ്രിമിറ്റീവ്സ് ആപേക്ഷിതം ആണ്. 

Hooks ഉപയോഗിച്ചു കൊണ്ട് നിങ്ങൾക്കു stateful ലോജിക് component ൽ നിന്ന് വേർതിരിച്ചു എഴുതാം. ഇതിലൂടെ നിങ്ങൾക്കു ഇത് ടെസ്റ്റ് ചെയ്യുവാനും ചെയാനും പുനരുപയോഗിക്കാനും സാധിക്കും. **Hooks ഉപയോഗിച്ച് Components ന്റെ അധികാരക്രമം മാറ്റാതെ തന്നെ നിങ്ങൾക്കു ലോജിക് പുനരുപയോഗിക്കാൻ ആവും വിധം എഴുതാൻ സാധിക്കും.** ഇത് കൊണ്ട് തന്നെ നിങ്ങൾ എഴുതുന്ന Hooks നിങ്ങളുടെ പ്രോജെക്ടിലെ മറ്റു components ഉം ആയിട്ടോ, മറ്റുള്ളവരുമായോ പങ്കുവെയ്ക്കാന്‍ എളുപ്പം ആണ്.
അടുത്ത അധ്യായം ആയ [Building Your Own Hooks](/docs/hooks-custom.html) ൽ നമുക്ക് ഇത് വിശദം ആയി കാണാം.  

### സങ്കീർണം ആയ Components മനസ്സിലാക്കാൻ ബുദ്ധിമുട്ടാണ് {#complex-components-become-hard-to-understand}

ഞങ്ങളുടെ അനുഭവത്തിൽ, ലളിതം ആയി തുടങ്ങുന്ന Components പലപ്പോഴും പിന്നീട് വലുതായി ലോജിക്കും സൈഡ് എഫക്ട് കൂടി കുഴഞ്ഞുമറിഞ്ഞ അവസ്ഥയിൽ എത്താറുണ്ട്. Lifecycle ഫങ്ക്ഷൻസിൽ ബന്ധം ഇല്ലാത്ത ലോജിക് കാലക്രമേണ കുമിഞ്ഞു കൂടുന്നു. ഉദാഹരണത്തിന്, `componentDidMount` ലും  `componentDidUpdate` ലും ഡാറ്റ കൊണ്ട് വരാൻ ഉള്ള ലോജിക്, `componentDidMount` ൽ തന്നെ എവെന്റ്റ് ലിസനേഴ്‌സ് സജ്ജമാകുകയും `componentWillUnmount` ൽ അവയെ നീക്കം ചെയുകയും ചെയാം. ബന്ധപെട്ടു കിടക്കുന്ന കോഡ് ഭാഗങ്ങൾ ദൂരേക്കു പോവുകയും, ബന്ധം കുറവ് ആയവ അടുത്ത് വരുന്നതും ശ്രദ്ധിക്കാം. ഇങ്ങനെ ഉള്ള സാഹചര്യങ്ങളിൽ തെറ്റു വരാൻ ഉള്ള സാധ്യത വളരെ അധികം വർധിക്കുന്നു.

ലോജിക് വർധിക്കുമ്പോൾ ഈ components നെ പിളർത്തി ചെറിയ ഭാഗങ്ങൾ ആകാൻ നേരത്തെതന്നെ Lifecycles ൽ ഉള്ള ലോജിക് സെഗ്മെന്റ്സ് തടസ്സം നിൽക്കാറുണ്ട്. ഇത് കൊണ്ട് കൂടി ആണ് സാധാരണ ആയി React നു ഒപ്പം ഒരു state management ലൈബ്രറി ഉപയോഗിക്കാൻ ആളുകൾ നിര്ബന്ധിതരാകുന്നത്. പക്ഷെ ഇതോടു കൂടി കോഡിലെ abstraction വർധിക്കുകയും, നിങ്ങൾക്കു ലോജിക് മാറ്റുവാൻ ആയി പല ഫയലുകൾ മാറി മാറി നോകേണ്ടതായും വരുന്നു.

Hooks ഉപയോഗിക്കുമ്പോൾ ആണെങ്കിൽ നിങ്ങൾക്കു ലോജിക് **ഉപയോഗം അനുസരിച്ചു പല പല ചെറിയ ഫങ്ക്ഷന്സ് രൂപത്തിലേക്ക് മാറ്റി എഴുതാൻ ആകും.**. എപ്പോൾ സംഭവിക്കുന്നു എന്നത് അല്ലാതെ എന്ത് ചെയുന്നു എന്നതിനെ ആധാരം ആക്കി നിങ്ങൾക്കു ലോജിക് എഴുതാവുന്നതു ആണ്.

പിന്നീട് [Using the Effect Hook](/docs/hooks-effect.html#tip-use-multiple-effects-to-separate-concerns) എന്ന അധ്യായത്തിൽ നമുക്കു ഇതേ കുറിച്ച് കൂടുതൽ നോക്കാം 

### Classes മനുഷ്യരേയും യന്ത്രങ്ങളെയും ആശയകുഴപ്പത്തിൽകുന്നു {#classes-confuse-both-people-and-machines}

കോഡ് പുനരുപയോഗം, കോഡ് ഓർഗനൈസേഷൻ എന്നിവക്കു കൂടുതൽ ബുദ്ധിമുട്ട് ഉണ്ടാക്കുന്നതിനു പുറമേ, ക്ലാസുകൾ മനസിലാക്കുക എന്നത് React പഠിക്കുന്നവർക് ഒരു വലിയ തടസ്സം ആണ് സൃഷ്ടിക്കുന്നത്. JavaScript ൽ ക്ലാസുകൾ മറ്റു പ്രോഗ്രാമിങ് ഭാഷകൾ നിന്ന് വിഭിന്നമായി പ്രവർത്തിക്കുന്നു, ഇതിന്റെ ഒരു ഉദാഹരണം ആണ് `this`. Babel ന്റെ സ്ഥിരത ആവാത്ത [syntax proposals](https://babeljs.io/docs/en/babel-plugin-transform-class-properties/) ഉപയോഗിച്ചില്ലെങ്കിൽ ഇത് തന്നെ വളരെ അധികം കോഡ് ലൈനുകൾ നീളും. Props, State, ഒരേ ദിശയിൽ അഴുക്കു തുടങ്ങിയ ആശയങ്ങൾ നന്നായി മനസിലായവക്ക് പോലും class ഒരു തടസ്സം ആയി നില്കുന്നത് കണ്ടിട്ടുണ്ട്. ഇത് കൂടാതെ എപ്പോഴാണ് ഫങ്ക്ഷന് അല്ലെങ്കിൽ ക്ലാസ് എഴുതേണ്ടത് എന്നത് മുതിർന്ന React ഡെവലപ്പേഴ്സിന് ഇടയിൽ പോലും തർക്കവിഷയം ആണ്.

<<<<<<< HEAD
React പുറത്തു വന്നിട്ടു ഇപ്പോൾ അഞ്ചു വര്ഷം ആകുന്നു, ഇനി ഉള്ള അഞ്ചു വർഷത്തേക്ക് കൂടി React ഉപയോഗം പ്രസക്തം ആയി നിൽക്കണം ഞങ്ങളുടെ ലക്ഷ്യം. [Svelte](https://svelte.technology/), [Angular](https://angular.io/), [Glimmer](https://glimmerjs.com/) എന്നീ ഫ്രെയിംവർക്കുകൾ തെളിയിച്ച പോലെ, [ahead-of-time compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) വളരെ അധികം സാധ്യത ഉള്ള ഒരു കൺസെപ്റ് ആണ്. പ്രിത്യേകിച് HTML ടെംപ്ലേറ്റുകൾ ഉണ്ടാകാൻ എന്നതിൽ ഉപരിയായി അതു ഉപയോഗിക്കുമ്പോൾ. ഈ അടുത്ത് ഞങ്ങൾ [Prepack](https://prepack.io/) ഉപയോഗിച്ച് [component folding](https://github.com/facebook/react/issues/7323) എന്ന ടെക്നോളജി React ൽ പരീക്ഷിച്ചു നോക്കുകയും, വളരെ നല്ല ഫലം കാണുകയും ഉണ്ടായി. പക്ഷെ പലപ്പോഴും Class കംപോണേന്റ്സ് ഉപയോഗിക്കുന്നത് പ്രവചിക്കാനാവാത്ത പരിണിതഫലങ്ങൾ ഉണ്ടാകുന്നതായി ഞങ്ങൾ കണ്ടു. ഇവക്കു പ്രതിവിധികൾ കൂടി ഉൾപെടുത്തുമ്പോൾ നമ്മൾ ചെയുന്ന പരീക്ഷണങ്ങൾ വേഗം കുറഞ്ഞു കിട്ടേണ്ട പ്രയോജനം ചെയുന്നു. ഇത് മാത്രം അല്ല Class എന്ന ഘടന പഴയ ബ്രൗസേഴ്സിന് വേണ്ടി വിവർത്തനം ചെയുമ്പോൾ കുറെ അധികം കോഡ് വരുന്നതായി കാണാം 
=======
In addition to making code reuse and code organization more difficult, we've found that classes can be a large barrier to learning React. You have to understand how `this` works in JavaScript, which is very different from how it works in most languages. You have to remember to bind the event handlers. Without [ES2022 public class fields](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields#public_instance_fields), the code is very verbose. People can understand props, state, and top-down data flow perfectly well but still struggle with classes. The distinction between function and class components in React and when to use each one leads to disagreements even between experienced React developers.
>>>>>>> 38bf76a4a7bec6072d086ce8efdeef9ebb7af227

ഇതിനു ഒരു പരിഹാരം എന്ന നിലയിൽ **Hooks നിങ്ങൾക്കു class ഉപയോഗിക്കാതെ തന്നെ React ന്റെ ഫീച്ചർസ് ഉപയോഗിക്കാം**. ആശയങ്ങളിൽ React Components എപ്പോഴും ഫങ്ക്ഷൻസിനോട് ആണ് അടുത്ത് നിന്നിട്ടുള്ളത്. Hooks ഉപയോഗിക്കുമ്പോൾ നിങ്ങൾക്കു ഫങ്ക്ഷന്സ് എഴുതുന്നതിന്റെ ഗുണങ്ങൾ React സ്വഭാവം ചോർന്നു പോകാതെ തന്നെ ഉപയോഗിക്കാം. പക്ഷെ ഹൂക്സ് ഉപയോഗിക്കാൻ ആയി നിങ്ങൾ സങ്കീർണം ആയ ഫങ്ക്ഷണൽ പ്രോഗ്രാമ്മിങ് ആശയങ്ങൾ പഠിക്കേണ്ടത് ഇല്ല. 

>ഉദാഹരണം:
>
>[Hooks ഒറ്റനോട്ടത്തിൽ](/docs/hooks-overview.html) പഠിച്ചു തുടങ്ങാം.

## ക്രമേണ ഉപയോഗം തുടങ്ങാം {#gradual-adoption-strategy}

>**TLDR: class React ൽ നിന്ന് ഒഴിവാകുന്നില്ല.**

React ഡെവലപ്പേഴ്‌സ് പലപ്പോഴും പുതിയ ഫീച്ചർസ് ഉപഭോക്താവിലേക്കു എത്തിക്കുന്ന തിരക്കിൽ ആയിരിക്കും. റിലീസ് ചെയുന്നു ഓരോ API യും അപ്പോൾ താനെ പഠിക്കാൻ ഈ തിരക്കിന് ഇടയിൽ അവസരം കിട്ടി എന്ന് വരില്ല. Hooks വളരെ പുതിയത് ആണ്, കുറച്ചു കൂടി കഴിഞ്ഞാൽ കൂടുതൽ നല്ല ട്യൂട്ടോറിയൽസ് പുറത്തു വരാൻ സാധ്യത ഉണ്ട്.

<<<<<<< HEAD
React ലെക് പുതിയ ഒരു ഫീച്ചർ കൂട്ടിച്ചേര്‍ക്കുക എന്ന് പറയുന്നത് വളരെ അധികം ശ്രദ്ധ അർപ്പിച്ചു ചെയ്യണ്ട കാര്യം ആണെന് ഞങ്ങൾ മനസിലാകുന്നു. അത് കൊണ്ട് തന്നെ ഒരു [RFC](https://github.com/reactjs/rfcs/pull/68) ലൂടെ ആണ് Hooks React ലേക് ചേർക്കാൻ ഉള്ള തീരുമാനം ഞങ്ങൾ എടുത്തത്. ഈ പേജിൽ നിങ്ങൾക്കു ഇതിന്റെ പ്രചോദനം, പിന്നിൽ നടന്ന ചർച്ചകൾ ഒക്കെ കാണാൻ സാധിക്കും.

ഇതിൽ എല്ലാം വളരെ മുഖ്യം ആയി ഒരു കാര്യം, **Hooks ഇപ്പോൾ നിങ്ങൾ എഴുതിയിരിക്കുന്ന class components നു ഒപ്പം ഉപയോഗിക്കാൻ ആകും** എന്നത് ആണ്. Hooks ലേക് മാറാൻ തിരക്കു കൂട്ടേണ്ട ആവശ്യകത ഇല്ല. Hooks ഉൾക്കൊള്ളിക്കാൻ ആയി നിങ്ങളുടെ നിലവിൽ ഉള്ള കോഡ്ബേസസ് മാറ്റി എഴുതേണ്ടത് ഇല്ല എന്ന് ആണ് ഞങ്ങളുടെ അഭിപ്രായം. Hooks എങ്ങനെ എഴുതാം എന്നതിനെ കുറിച്ച് സംഘത്തിലെ അല്ല ഡെവലപ്പേഴ്സിനും ഒരു പരിശീലനം ആവശ്യം ആയി വരാം. ഞങ്ങളുടെ അനുഭവത്തിൽ ചെറിയ components Hooks ലേക് മാറ്റി എഴുതി തുടങ്ങുന്നത് ആണ് എപ്പോഴും നല്ലത്. നിങ്ങൾ Hooks ഉപയോഗിച്ചു നോക്കി എങ്കിൽ ഞങ്ങളെ നിങ്ങളുടെ [അഭിപ്രായം](https://github.com/facebook/react/issues/new) അറിയിക്കാൻ മറക്കരുത്.
=======
We also understand that the bar for adding a new primitive to React is extremely high. For curious readers, we have prepared a [detailed RFC](https://github.com/reactjs/rfcs/pull/68) that dives into the motivation with more details, and provides extra perspective on the specific design decisions and related prior art.

**Crucially, Hooks work side-by-side with existing code so you can adopt them gradually.** There is no rush to migrate to Hooks. We recommend avoiding any "big rewrites", especially for existing, complex class components. It takes a bit of a mind shift to start "thinking in Hooks". In our experience, it's best to practice using Hooks in new and non-critical components first, and ensure that everybody on your team feels comfortable with them. After you give Hooks a try, please feel free to [send us feedback](https://github.com/facebook/react/issues/new), positive or negative.
>>>>>>> 38bf76a4a7bec6072d086ce8efdeef9ebb7af227

Hooks ഇപ്പോൾ class ഉപയോഗിക്കാവുന്ന അല്ല ഉപയോഗ മേഖലകളും ഉൾകൊള്ളിക എന്നതാണ് ഞങ്ങളുടെ ഉദ്ദേശം. എങ്കിൽ കൂടി **class components React ൽ നിന്ന് ഒഴിവാക്കാൻ ഉള്ള പ്ലാൻ ഇല്ല**. ഫേസ്ബുക്കിൽ പതിനായിരം വരെ components class വച്ച് ആണ് എഴുതിയിരിക്കുന്നത്. അവയെലാം ഇപ്പോൾ തന്നെ മാറ്റി എഴുതാൻ ആകുകയും ഇല്ല. അതെ സമയം ഇനി Hooks class ന് ഒപ്പം തന്നെ ഉപയോഗിച്ച് പോവുക എന്നത് ആണ് ഞങ്ങൾ ചെയാൻ പോകുന്നത് 

## പതിവ് ചോദ്യങ്ങൾ {#frequently-asked-questions}

ഞങ്ങൾ hooks ഇനെ കുറിച്ച് ഉള്ള [പതിവ് ചോദ്യങ്ങളുടെ പട്ടിക](/docs/hooks-faq.html) തയാറാക്കിയിട്ടുണ്ട്.

## അടുത്ത ഘട്ടങ്ങൾ {#next-steps}

ഈ പേജ് അവസാനിക്കുന്നതോടെ നിങ്ങൾക്കു എന്തൊക്കെ പ്രശ്നങ്ങൾ ആണ് hooks പരിഹരിക്കുന്നത് എന്നതിന്റെ ഒരു ഏകദേശ രൂപം കിട്ടി കാണും. ഇനി എങ്ങനെ നിങ്ങൾക്കു hooks ഉപയോഗിക്കാം എന്ന് [അടുത്ത പേജ്](/docs/hooks-overview.html) മുതൽ വായിക്കാം. അവിടെ നമ്മൾ ഉദാഹരണങ്ങളിലൂടെ hooks ഉപയോഗിക്കാൻ പഠിക്കും.
