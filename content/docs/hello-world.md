---
id: hello-world
title: ഹലോ, വേൾഡ്
permalink: docs/hello-world.html
prev: cdn-links.html
next: introducing-jsx.html
---

വളരെ ചെറിയ ഒരു ഉദാഹരണം നോക്കാം:

```jsx
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<h1>Hello, world!</h1>);
```

"Hello, world!" എന്നൊരു തലക്കെട്ടു നിങ്ങൾക്കു ഇപ്പോൾ പേജിൽ കാണാം.

**[Try it on CodePen](https://codepen.io/gaearon/pen/rrpgNB?editors=1010)**

ഒരു ഓൺലൈൻ എഡിറ്റർ തുറക്കാൻ മുകളിലുള്ള ലിങ്ക് ക്ലിക്കുചെയ്യുക. ചില മാറ്റങ്ങൾ വരുത്താൻ മടിക്കേണ്ടതില്ല, അവ ഔട്പുട്ടിനെ എങ്ങനെ ബാധിക്കുന്നുവെന്നത് കാണുക. ഈ ഗൈഡിലെ മിക്ക പേജുകളും ഇതിനുള്ള എഡിറ്റബിൾ ഉദാഹരണങ്ങൾ ഉണ്ടായിരിക്കും.


## ഗൈഡ് വായിക്കേണ്ട രീതി {#how-to-read-this-guide}


ഈ ഗൈഡിൽ നമ്മൾ React ആപ്ലിക്കേഷനുകളുടെ നിർമാണ ബ്ലോക്കുകൾ പരിശോധിക്കും: Elements & Components. നിങ്ങൾക്കു ഈ പുനരുപയോഗിക്കാവുന്ന ചെറിയ കഷ്ണങ്ങൾ നിന്ന് നിങ്ങൾക്ക് സങ്കീർണ്ണമായ ആപ്ലിക്കേഷനുകൾ സൃഷ്ടിക്കാൻ കഴിയും.

>ടിപ്പ്
>
>ഈ ഗൈഡ്, **സ്റ്റെപ്പ് മുഖേനയുള്ള പഠന ആശയങ്ങൾ** തിരഞ്ഞെടുക്കുന്നവരെ ഉദ്ദേശിച്ചുള്ളതാണ്. പഠിക്കുന്നതിലൂടെ പഠിക്കാൻ നിങ്ങൾ തിരഞ്ഞെടുക്കുകയാണെങ്കിൽ ഞങ്ങളുടെ [ട്യൂട്ടോറിയൽ](/tutorial/tutorial.html) പരിശോധിക്കുക. ഗൈഡും ട്യൂട്ടോറിയലും പരസ്പരം കോംപ്ലาമെന്റ് ചെയ്യുന്നതായി നിങ്ങൾക്കു കാണാം.

പ്രധാന React ആശയങ്ങളെക്കുറിച്ചുള്ള ഘട്ടം ഘട്ടമായുള്ള ഗൈഡിലെ ആദ്യ അധ്യായം ഇതാണ്. നാവിഗേഷൻ സൈറ്റിലെ എല്ലാ അദ്ധ്യായങ്ങളുടേയും ഒരു പട്ടിക കാണാം. നിങ്ങൾ ഒരു മൊബൈൽ ഉപകരണത്തിൽ നിന്ന് ഇത് വായിച്ചാൽ, നിങ്ങളുടെ സ്ക്രീനിന്റെ ചുവടെ വലത് കോണിലുള്ള ബട്ടൺ അമർത്തി നാവിഗേഷൻ ആക്സസ് ചെയ്യാവുന്നതാണ്.

മുൻ അധ്യായങ്ങളിൽ അവതരിപ്പിച്ചിരിക്കുന്ന അറിവുകളെ അടിസ്ഥാനമാക്കി ആണ് ഈ പാഠഭാഗം നിർമിച്ചിരിക്കുന്നത്. **React നെ കുറിച്ച് ഉള്ള ഭൂരിഭാഗം കാര്യങ്ങളും സൈഡ്ബാറിലെ "Main Concepts" ൽ ഉള്ള അധ്യായങ്ങൾ അതേ ക്രമത്തിൽ വായിച്ചാൽ മനസിലാക്കാം.** ഉദാഹരണത്തിന്, [“Introducing JSX”](/docs/introducing-jsx.html) ആണ് അടുത്ത അധ്യായം.

## മുൻപേ അറിയേണ്ട കാര്യങ്ങൾ {#knowledge-level-assumptions}

React ഒരു JavaScript ലൈബ്രറി ആണ്, അതിനാൽ നമ്മൾ JavaScript ഭാഷയെ കുറിച്ചുള്ള അടിസ്ഥാന ധാരണയുള്ളതായി കരുതുന്നു. **നിങ്ങൾക്കു ആത്മവിശ്വാസം കുറവാണെങ്കിൽ ഈ ട്യൂട്ടോറിയൽ [going through a JavaScript tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript) ചെയ്തു നോക്കാവുന്നത് ആണ്**. അരമണിക്കൂർ തൊട്ടു ഒരു മണിക്കൂർ വരെ ദൈർക്യം ഉള്ള ഈ tutorial ചെയ്താൽ നിങ്ങൾക്കു React ഉം JavaScript ഉം ഒരുമിച്ചു പഠിക്കുന്നതിന്റെ കാഠിന്യം ഒഴിവാക്കാം.

>കുറിപ്പ്
>
<<<<<<< HEAD
>ഈ ഗൈഡ് പുതിയ JavaScript syntax ഉദാഹരണങ്ങളിൽ ഉപയോഗിച്ചിട്ടുണ്ട്. JavaScript ഉപയോഗിച്ചിട്ട് കുറച്ചു വർഷങ്ങൾ ആയി എങ്കിൽ, [ഈ മൂന്ന് പോയിന്റുകൾ](https://gist.github.com/gaearon/683e676101005de0add59e8bb345340c) വായിക്കുന്നത് നല്ലതായിരിക്കും.
=======
>This guide occasionally uses some newer JavaScript syntax in the examples. If you haven't worked with JavaScript in the last few years, [these three points](https://gist.github.com/gaearon/683e676101005de0add59e8bb345340c) should get you most of the way.
>>>>>>> 26a870e1c6e232062b760d37620d85802750e985


## നമുക്കു തുടങ്ങാം! {#lets-get-started}

ഇതിനു താഴെ website footer ൽ നിങ്ങൾക്കു [അടുത്ത അദ്ധ്യായത്തിന്റെ ലിങ്ക്](/docs/introducing-jsx.html) ലഭ്യമാണ് 


