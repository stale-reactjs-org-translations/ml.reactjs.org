---
id: add-react-to-a-website
title: ഒരു വെബ്‌സൈറ്റിൽ React ചേർക്കാം
permalink: docs/add-react-to-a-website.html
redirect_from:
  - "docs/add-react-to-an-existing-app.html"
prev: getting-started.html
next: create-a-new-react-app.html
---

ആവശ്യാനുസരണം React ഉപയോഗിക്കൂ.

ക്രമേണയുള്ള നവീകരണങ്ങൾ മുന്നിൽ കണ്ട് കൊണ്ടാണ് React തുടക്കം മുതൽ ഡിസൈൻ ചെയ്തിരിക്കുന്നത്, **വളരെ കുറഞ്ഞ തോതിലോ അല്ലെങ്കിൽ ആവശ്യമുള്ള അത്രയും അളവിലോ** നിങ്ങൾക്ക് React ഉപയോഗിക്കാം. ഒരുപക്ഷേ നിങ്ങൾക്ക് ഒരല്പം യൂസർ ഇന്ററാക്ഷൻ  ഒരു പേജിൽ ചേർക്കണമായിരിക്കാം. അത് ചെയ്യുന്നതിനുള്ള ഏറ്റവും മികച്ച മാർഗ്ഗമാണ് React Components.

ഒട്ടുമിക്ക വെബ്‌സൈറ്റുകളും സിംഗിൾ പേജ് ആപ്പുകൾ ആയിക്കൊള്ളണമെന്നില്ല. **വളരെ ചുരുങ്ങിയ വരികൾ ഉപയോഗിച്ച് ഏതൊരു ബിൽഡ് ടൂളിന്റെയും സഹായമില്ലാതെ** നിങ്ങളുടെ വെബ്‌സൈറ്റിലെ ഒരു ചെറിയ ഭാഗത്ത് React പരീക്ഷിച്ചു നോക്കാം. സാവധാനം നിങ്ങൾക്ക് അതിന്റെ ഉപയോഗം കൂട്ടിക്കൊണ്ട് വരാം അല്ലെങ്കിൽ മാറിക്കൊണ്ടിരിക്കുന്ന ഡൈനാമിക് widget-കളിൽ മാത്രമായി അവയെ ഒതുക്കി നിർത്താം.

---

- [ഒരു മിനിറ്റിൽ React കൂട്ടിച്ചേർക്കാം](#add-react-in-one-minute)
- [JSX ഉപയോഗിച്ചുള്ള React പരീക്ഷിക്കാം (നിർബന്ധമില്ല)](#optional-try-react-with-jsx) (bundler ആവശ്യമില്ല!)

## ഒരു മിനിറ്റിൽ React കൂട്ടിച്ചേർക്കാം {#add-react-in-one-minute}

നിലവിലുള്ള ഒരു HTML പേജിൽ എങ്ങനെ React ചേർക്കാം എന്ന് നോക്കാം. നിങ്ങൾക്ക് സ്വന്തം വെബ്സൈറ്റോ അല്ലെങ്കിൽ പരിശീലനത്തിനായി ഒരു പുതിയ HTML ഫയലോ ഉപയോഗിക്കാം.

സങ്കീർണ്ണമായ ടൂളുകളോ ഇൻസ്റ്റാലേഷനുകളോ ഇതിനാവശ്യമില്ല -- **ഈ ഭാഗം പൂർത്തിയാക്കുന്നതിനു ഒരു ഇന്റർനെറ്റ് കണക്ഷനും നിങ്ങളുടെ ഒരല്പം സമയവും  മാത്രം മതി.**

<<<<<<< HEAD
നിങ്ങളുടെ താല്പര്യാർത്ഥം [മുഴുവൻ ഉദാഹരണം (2KB zip ഫയൽ) ഡൌൺലോഡ് ചെയ്യാം](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/f6c882b6ae18bde42dcf6fdb751aae93495a2275.zip)
=======
Optional: [Download the full example (2KB zipped)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/87f0b6f34238595b44308acfb86df6ea43669c08.zip)
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

### സ്റ്റെപ് 1 : HTML-ലേക്ക് ഒരു DOM കണ്ടെയ്നർ ആഡ് ചെയ്യാം {#step-1-add-a-dom-container-to-the-html}

ആദ്യമായി മാറ്റം വരുത്തേണ്ട HTML പേജ് തുറന്ന ശേഷം React ഉപയോഗിക്കാൻ പോകുന്ന സ്ഥലം അടയാളപ്പെടുത്തുന്നതിനായി ഒരു `<div>` ടാഗ് ചേർക്കുക.
ഉദാഹരണം:

```html{3}
<!-- ... നിലവിലുള്ള HTML ... -->

<div id="like_button_container"></div>

<!-- ... നിലവിലുള്ള HTML ... -->
```

ഈ `<div>`-നു നമ്മൾ HTML-ന്റെ `id` attribute സമാനതകളില്ലാത്ത രീതിയിൽ നൽകിയിട്ടുണ്ട്. അത് വഴി JavaScript കോഡ് ഉപയോഗിച്ച് ഇത് കണ്ടെത്താനും അതിനകത്തു ഒരു React component കാണിക്കുന്നതിനും സഹായിക്കുന്നു.

>നുറുങ്ങു വിദ്യ
>
>ഇത്തരത്തിൽ ഒരു "കണ്ടെയ്‌നർ" `<div>` ഒരു `<body>` ടാഗിനകത്ത് **എവിടെ വേണമെങ്കിലും** നിങ്ങൾക്ക് ഉപയോഗിക്കാൻ സാധിക്കും. ഒരു പേജിൽ തന്നെ നിങ്ങൾക്ക് ആവശ്യമുള്ള അത്ര സ്വാതന്ത്ര്യ DOM കണ്ടെയ്നറുകൾ ഉണ്ടാക്കാം. സാധാരണയായി അവ കാലിയായിരിക്കും. -- DOM കണ്ടെയ്നറുകളുടെ ഉള്ളടക്കത്തിൽ React-നു മാറ്റങ്ങൾ വരുത്താൻ സാധിക്കും.

### സ്റ്റെപ് 2: Script ടാഗുകൾ ചേർക്കാം {#step-2-add-the-script-tags}

അടുത്തതായി HTML പേജിൽ `</body>` ടാഗ് ക്ലോസ് ചെയ്യുന്നതിന് മുൻപായി നമുക്ക് 3 `<script>` ടാഗുകൾ എഴുതിക്കിച്ചേർക്കാം:

```html{5,6,9}
  <!-- ... മറ്റു HTML കോഡുകൾ ... -->

<<<<<<< HEAD
  <!-- React ലോഡ് ചെയ്യുന്നു. -->
  <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
=======
  <!-- Load React. -->
  <!-- Note: when deploying, replace "development.js" with "production.min.js". -->
  <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

  <!-- നമ്മുടെ React component ലോഡ് ചെയ്യുന്നു. -->
  <script src="like_button.js"></script>

</body>
```

ആദ്യത്തത്തെ 2 ടാഗുകൾ React ലോഡ് ചെയ്യുമ്പോൾ മൂന്നാമത്തെ ടാഗ് നിങ്ങളുടെ component ലോഡ് ചെയ്യുന്നു.

### സ്റ്റെപ് 3: ഒരു React Component ഉണ്ടാക്കാം {#step-3-create-a-react-component}

നിങ്ങളുടെ HTML പേജിനു അടുത്തായി `like_button.js` എന്നൊരു ഫയൽ ഉണ്ടാക്കുക.

**[ഈ സ്റ്റാർട്ടർ കോഡ്](https://gist.github.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)** തുറന്ന ശേഷം നിങ്ങൾ ഇപ്പോൾ ഉണ്ടാക്കിയ ഫയലിൽ അത് പേസ്റ്റ് ചെയ്യുക.

>നുറുങ്ങു വിദ്യ
>
>ഈ കോഡിൽ `LikeButton` എന്നൊരു React Component നമ്മൾ ഉണ്ടാക്കിയിരിക്കുന്നു. നിങ്ങൾക്ക് ഒന്നും മനസ്സിലായില്ലെങ്കിലും സാരമില്ല -- React-ന്റെ ബിൽഡിങ് ബ്ലോക്കുകളെ പറ്റി ഇനി വരുന്ന [പ്രായോഗിക ട്യൂട്ടോറിയലി](/tutorial/tutorial.html)ലും [പ്രധാന ആശയങ്ങളുടെ ഗൈഡി](/docs/hello-world.html)ലും നമ്മൾ പഠിച്ചെടുക്കും. ഇപ്പോഴത്തേക്ക് നമുക്ക് ഇത് സ്‌ക്രീനിൽ വരുത്താൻ നോക്കാം.

<<<<<<< HEAD
**[ഈ സ്റ്റാർട്ടർ കോഡ്](https://gist.github.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)**-നു ശേഷം `like_button.js` ഫയലിൽ താഴെയായി രണ്ട് വരി കൂടി ചേർക്കുക.

```js{3,4}
// ... നിങ്ങൾ പേസ്റ്റ് ചെയ്ത ഭാഗം ...
=======
After **[the starter code](https://gist.github.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)**, add three lines to the bottom of `like_button.js`:

```js{3,4,5}
// ... the starter code you pasted ...
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

const domContainer = document.querySelector('#like_button_container');
const root = ReactDOM.createRoot(domContainer);
root.render(e(LikeButton));
```

<<<<<<< HEAD
ഈ രണ്ട് വരികൾ നമ്മൾ ആദ്യത്തെ സ്റ്റെപ്പിൽ ചേർത്ത `<div>` കണ്ടെത്തുകയും നമ്മുടെ "ലൈക്ക്" ബട്ടൺ React component അതിനകത്ത് കാണിക്കുകയും ചെയ്യുന്നു.
=======
These three lines of code find the `<div>` we added to our HTML in the first step, create a React app with it, and then display our "Like" button React component inside of it.
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

### അത്രയേ ഉള്ളൂ! {#thats-it}

ഇനി നാലാമതൊരു സ്റ്റെപ് ഇല്ല. **നിങ്ങളുടെ വെബ്‌സൈറ്റിൽ നിങ്ങൾ ആദ്യത്തെ React component കൂട്ടിച്ചേർത്തിരിക്കുന്നു**

React ഉപയോഗിക്കുമ്പോൾ ചെയ്തു നോക്കാവുന്ന കൂടുതൽ നുറുങ്ങു വിദ്യകൾക്ക് ഇനി വരുന്ന ഭാഗങ്ങൾ നോക്കാവുന്നതാണ്.

**[ഈ ഉദാഹരണത്തിന്റെ മുഴുവനായുള്ള സോഴ്സ് കോഡ്](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605)**

<<<<<<< HEAD
**[ഈ ഉദാഹരണം ഡൌൺലോഡ് ചെയ്യാം (2KB zipped)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/f6c882b6ae18bde42dcf6fdb751aae93495a2275.zip)**
=======
**[Download the full example (2KB zipped)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/87f0b6f34238595b44308acfb86df6ea43669c08.zip)**
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

### നുറുങ്ങു വിദ്യ: ഒരു Component വീണ്ടും വീണ്ടും ഉപയോഗിക്കാം {#tip-reuse-a-component}

സാധാരണയായി ഒരു പേജിൽ തന്നെ ഒന്നിലധികം സ്ഥലങ്ങളിൽ നിങ്ങള്ക്ക് ഒരു  React component കാണിക്കേണ്ടി വരും. നമ്മുടെ "Like" ബട്ടൺ എങ്ങനെ 3 സ്ഥലങ്ങളിൽ കാണിക്കാം എന്നും അതിലേക്ക് എങ്ങനെ ഡാറ്റ അയച്ചു കൊടുക്കാം എന്നും നമുക്ക് നോക്കാം.

[ഈ ഉദാഹരണത്തിന്റെ മുഴുവനായുള്ള സോഴ്സ് കോഡ്](https://gist.github.com/gaearon/faa67b76a6c47adbab04f739cba7ceda)

<<<<<<< HEAD
[ഈ ഉദാഹരണം ഡൌൺലോഡ് ചെയ്യാം (2KB zipped)](https://gist.github.com/gaearon/faa67b76a6c47adbab04f739cba7ceda/archive/9d0dd0ee941fea05fd1357502e5aa348abb84c12.zip)
=======
[Download the full example (2KB zipped)](https://gist.github.com/gaearon/faa67b76a6c47adbab04f739cba7ceda/archive/279839cb9891bd41802ebebc5365e9dec08eeb9f.zip)
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

>കുറിപ്പ്
>
>React ഉപയോഗിക്കുന്ന ഭാഗങ്ങൾ പരസ്പരം ബന്ധമില്ലാതെ ഇരിക്കുന്ന ഘട്ടങ്ങളിൽ ആണ് ഈ രീതി അവലംബിച്ചു പോരുന്നത്. React കോഡിന് അകത്ത്  [component കോമ്പോസിഷൻ](/docs/components-and-props.html#composing-components) ഉപയോഗിക്കുന്നതായിരിക്കും കൂടുതൽ എളുപ്പം.

### നുറുങ്ങു വിദ്യ: പ്രൊഡക്ഷൻ സാഹചര്യങ്ങൾക്ക് വേണ്ടി JavaScript Minify ചെയ്യാം. {#tip-minify-javascript-for-production}

നിങ്ങളുടെ വെബ്‌സൈറ്റ് പ്രൊഡക്ഷൻ സെർവറിൽ ഡിപ്ലോയ് ചെയ്യുമ്പോൾ Minify ചെയ്യാത്ത JavaScript കോഡ് പേജിന്റെ വേഗത കുറയ്ക്കും എന്ന കാര്യം ഓർത്തിരിക്കുക.

നിങ്ങളുടെ അപ്ലിക്കേഷൻ സ്ക്രിപ്റ്റുകൾ Minify രൂപത്തിൽ ആണെങ്കിൽ അവ പ്രൊഡക്ഷനിൽ ഇടാൻ തയ്യാറായി ഇരിക്കുകയാണ്. നിങ്ങൾ ഡിപ്ലോയ് ചെയ്തിരിക്കുന്ന HTML ലോഡ് ചെയുന്നത് `production.min.js` എന്ന പേരിൽ അവസാനിക്കുന്ന React-ന്റെ പുതിയ പതിപ്പാണെന്നു ഉറപ്പു വരുത്തുക:

```js
<script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
```

നിങ്ങളുടെ script-കൾക്ക് ഒരു മിനിഫിക്കേഷൻ സ്റ്റെപ് ഇല്ല എന്നുണ്ടെങ്കിൽ [ഇവിടെ നോക്കാവുന്നതാണ്](https://gist.github.com/gaearon/42a2ffa41b8319948f9be4076286e1f3).

## JSX ഉപയോഗിച്ചുള്ള React പരീക്ഷിക്കാം (നിർബന്ധമില്ല) {#optional-try-react-with-jsx}

<<<<<<< HEAD
മുകളിലത്തെ ഉദാഹരണങ്ങളിൽ വെബ് ബ്രൗസറുകൾക്ക് സ്വതഃസിദ്ധമായി ഉള്ള കഴിവുകളെ മുന്നിൽ കണ്ട് കൊണ്ടാണ് നമ്മൾ കോഡ് എഴുതിയത്. അത് കൊണ്ടാണ് നമുക്ക് React എന്ത് കാണിക്കണം എന്ന് പറയാൻ ഒരു JavaScript function വിളിക്കേണ്ടി വന്നത്.
=======
In the examples above, we only relied on features that are natively supported by browsers. This is why we used a JavaScript function call to tell React what to display:
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

```js
const e = React.createElement;

// ഒരു "Like" ബട്ടൺ കാണിക്കാൻ <button>
return e(
  'button',
  { onClick: () => this.setState({ liked: true }) },
  'Like'
);
```

എന്നിരുന്നാലും, [JSX](/docs/introducing-jsx.html) ഉപയോഗിക്കാൻ ഉള്ള ഉപാധിയും React നൽകുന്നുണ്ട്.

```js
// ഒരു "Like" ബട്ടൺ കാണിക്കാൻ <button>
return (
  <button onClick={() => this.setState({ liked: true })}>
    Like
  </button>
);
```

ഈ രണ്ട് കോഡുകളും ഒരേ ആവശ്യത്തിനുള്ളതാണ്. **JSX ഉപയോഗിക്കണം എന്ന് [യാതൊരു നിർബന്ധവുമില്ല](/docs/react-without-jsx.html)**, എന്നാൽ React-നോടൊപ്പമോ അല്ലെങ്കിൽ മറ്റു ലൈബ്രറികൾ വഴിയോ UI കോഡുകൾ എഴുതുവാൻ നിരവധി ആളുകൾ ഇത് ഉപയോഗിക്കുന്നുണ്ട്.

<<<<<<< HEAD
നിങ്ങൾക്ക് [ഈ ഓൺലൈൻ കൺവെർട്ടർ](https://babeljs.io/en/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=DwIwrgLhD2B2AEcDCAbAlgYwNYF4DeAFAJTw4B88EAFmgM4B0tAphAMoQCGETBe86WJgBMAXJQBOYJvAC-RGWQBQ8FfAAyaQYuAB6cFDhkgA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.4.3) ഉപയോഗിച്ച് JSX പരീക്ഷിച്ചു നോക്കാം.
=======
You can play with JSX using [this online converter](https://babeljs.io/en/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=DwIwrgLhD2B2AEcDCAbAlgYwNYF4DeAFAJTw4B88EAFmgM4B0tAphAMoQCGETBe86WJgBMAXJQBOYJvAC-RGWQBQ8FfAAyaQYuAB6cFDhkgA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.15.7).
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

### വേഗത്തിൽ JSX പരിശോധിക്കാം {#quickly-try-jsx}

നിങ്ങളുടെ പ്രോജെക്ടിൽ JSX ചേർക്കുന്നതിനുള്ള ഏറ്റവും വേഗമേറിയ മാർഗ്ഗം എന്നത് ഈ `<script>` ടാഗ് പേജിൽ ഇടുക എന്നതാണ്.

```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

<<<<<<< HEAD
`type="text/babel"` എന്ന attribute ചേർത്ത് നിങ്ങൾക്ക് ഏതൊരു `<script>` ടാഗിന്റെ കൂടെയും JSX ഉപയോഗിക്കാം. ഉദാഹരണത്തിന് നിങ്ങൾക്ക് [JSX ഉള്ള ഈ HTML ഫയൽ](https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html) ഡൌൺലോഡ് ചെയ്ത് പരീക്ഷിച്ചു നോക്കാവുന്നതാണ്.
=======
Now you can use JSX in any `<script>` tag by adding `type="text/babel"` attribute to it. Here is [an example HTML file with JSX](https://raw.githubusercontent.com/reactjs/reactjs.org/main/static/html/single-file-example.html) that you can download and play with.
>>>>>>> 8223159395aae806f8602de35e6527d35260acfb

ലളിതമായ ഡെമോകൾ ഉണ്ടാക്കുന്നതിനും പഠിക്കുന്നതിനും ഈ രീതി മതിയാകും. എന്നാൽ ഇത് നിങ്ങളുടെ വെബ്‌സൈറ്റിന്റെ വേഗത കുറക്കുന്നതിനാൽ **പ്രൊഡക്ഷൻ സാഹചര്യങ്ങൾക്ക് അനുകൂലമല്ല**. നിങ്ങൾ മുന്നോട്ട് പോകുന്നതിനനുസരിച്ച് ഈ പുതിയ `<script>` ടാഗുകളും `type="text/babel"` എന്ന attribute-കളും നമ്മൾ നീക്കം ചെയ്യും. പകരം, അടുത്ത ഭാഗത്തിൽ നമ്മൾ ഒരു JSX പ്രീപ്രോസസ്സർ ഉപയോഗിച്ച്‌ എല്ലാ `<script>` ടാഗുകളെയും കൺവേർട്ട് ചെയ്യും.

### ഒരു പ്രോജെക്ടിൽ JSX ചേർക്കാം {#add-jsx-to-a-project}

ഒരു പ്രോജെക്ടിൽ JSX ചേർക്കുന്നതിന് bundler പോലെ സങ്കീർണ്ണമായ ടൂളുകളോ ഒരു ഡെവലപ്മെന്റ് സെർവറോ ആവശ്യമില്ല. JSX ചേർക്കുന്നത് **CSS പ്രീപ്രോസസ്സർ ചേർക്കുന്നതിന് സമാനമാണ്**. നിങ്ങളുടെ കമ്പ്യൂട്ടറിൽ [Node.js](https://nodejs.org/) ഇൻസ്റ്റാൾ ചെയ്തിട്ടുണ്ടാകണം എന്ന് മാത്രം.

നിങ്ങളുടെ പ്രൊജക്റ്റ് ഫോൾഡറിൽ ടെർമിനൽ തുറന്ന ശേഷം ഈ രണ്ട് കമന്റുകൾ പേസ്റ്റ് ചെയ്യുക.

1. **സ്റ്റെപ് 1:** `npm init -y` എന്ന് റൺ ചെയ്യുക (അത് പരാജയപ്പെടുകയാണെങ്കിൽ, [ഇവിടെ പരിഹാരം കണ്ടെത്താം](https://gist.github.com/gaearon/246f6380610e262f8a648e3e51cad40d))
2. **സ്റ്റെപ് 2:** `npm install babel-cli@6 babel-preset-react-app@3` എന്ന് റൺ ചെയ്യുക

>നുറുങ്ങു വിദ്യ
>
>നമ്മൾ ഇവിടെ **npm ഉപയോഗിച്ചത് JSX പ്രീപ്രോസസ്സർ ഇൻസ്റ്റാൾ ചെയ്യാൻ മാത്രമാണ്;** നമുക്ക് മറ്റൊന്നിനും അത് ആവശ്യമില്ല. React-ഉം അപ്ലിക്കേഷൻ കോഡും `<script>` ടാഗ് വെച്ച് അത് പോലെ നിലനിർത്താം.

അഭിനന്ദനങ്ങൾ! നിങ്ങൾ **പ്രൊഡക്ഷനുതകുന്ന ഒരു JSX രൂപം** നിങ്ങളുടെ പ്രോജെക്ടിലേക്ക് കൂട്ടിച്ചേർത്തിരിക്കുന്നു.


### JSX പ്രീപ്രോസസ്സർ റൺ ചെയ്യാം {#run-jsx-preprocessor}

`src` എന്നൊരു ഫോൾഡർ ഉണ്ടാക്കിയ ശേഷം ഈ ടെർമിനൽ കമാൻഡ് റൺ ചെയ്യുക:

```console
npx babel --watch src --out-dir . --presets react-app/prod
```

>കുറിപ്പ്
>
>`npx` എന്നത് ടൈപ്പ് ചെയ്തപ്പോൾ തെറ്റിയതല്ല -- അത് [npm 5.2-നു മുകളിൽ ഉള്ള പതിപ്പുകളോടൊപ്പം വരുന്ന ഒരു പാക്കേജ് റണ്ണർ ടൂൾ](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) ആണ്.
>
>"`babel` പാക്കേജ് നിങ്ങൾ തെറ്റായി ഇൻസ്റ്റാൾ ചെയ്തതായിരിക്കാം" എന്ന എറർ സന്ദേശം വരികയാണെങ്കിൽ നിങ്ങൾ [തൊട്ടു മുൻപുള്ള സ്റ്റെപ്](#add-jsx-to-a-project) വിട്ടു പോയിട്ടുണ്ടാകാം. ഇതേ ഫോൾഡറിൽ അത് ചെയ്ത ശേഷം വീണ്ടും ശ്രമിക്കുക.

ഇത് തീരുന്നതിനായി കാത്തു നിൽക്കണമെന്നില്ല -- ഈ കമാൻഡ് ഒരു ഓട്ടോമേറ്റഡ് വാച്ചർ സ്റ്റാർട്ട് ചെയ്യുന്നുണ്ട്.

ഈ **[JSX സ്റ്റാർട്ടർ കോഡ്](https://gist.github.com/gaearon/c8e112dc74ac44aac4f673f2c39d19d1/raw/09b951c86c1bf1116af741fa4664511f2f179f0a/like_button.js)** ഉപയോഗിച്ച്   `src/like_button.js` എന്ന ഫയൽ ക്രിയേറ്റ് ചെയ്‌താൽ, വാച്ചർ ബ്രൗസറിന് അനുയോജ്യമായ രീതിയിൽ plain JavaScript കോഡ് ഉപയോഗിച്ച് പ്രീപ്രോസസ്സ് ആയിട്ടുള്ള `like_button.js` ഉണ്ടാക്കിയെടുക്കും. നിങ്ങൾ സോഴ്സ് ഫയൽ JSX-ഇൽ മാറ്റം വരുത്തുമ്പോൾ ഈ രൂപാന്തരം തനിയെ വീണ്ടും ഓടുന്നതായിരിക്കും.

ഒരു ബോണസ് എന്ന രീതിയിൽ പഴയ ബ്രൗസറുകളിലും പൊട്ടാത്ത രീതിയിൽ ഇത് നിങ്ങളെ ക്ലാസ്സുകൾ പോലെയുള്ള ഏറ്റവും പുതിയ JavaScript പദവിന്യാസങ്ങൾ ഉപയോഗിക്കാൻ സഹായിക്കുന്നു. നമ്മൾ ഇപ്പോൾ ഉപയോഗിച്ചത് Babel എന്ന ടൂൾ ആണ്. ഇതിനെ കുറിച്ച് കൂടുതൽ പഠിക്കാൻ [ഇതിന്റെ ഡോക്യൂമെന്റഷൻ](https://babeljs.io/docs/en/babel-cli/) നോക്കാവുന്നതാണ്.

നിങ്ങൾക്ക് ബിൽഡ് ടൂളുകൾ കൂടുതൽ എളുപ്പമായി തോന്നിത്തുടങ്ങുന്നുണ്ടെങ്കിൽ അവ ഉപയോഗിച്ച്‌ കൂടുതൽ കാര്യങ്ങൾ ചെയ്യാൻ [അടുത്ത ഭാഗം](/docs/create-a-new-react-app.html) നിങ്ങളെ സഹായിക്കും. അതിൽ ഏറ്റവും പ്രശസ്തമായ ടൂൾചെയിനുകളെ പറ്റി പ്രതിപാദിക്കുന്നുണ്ട്. അത് നിങ്ങൾക്ക് ബുദ്ധിമുട്ടാണെങ്കിൽ ഇപ്പോഴുള്ള script ടാഗുകൾ തന്നെ മതിയാകും.
