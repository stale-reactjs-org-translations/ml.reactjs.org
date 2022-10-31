---
id: create-a-new-react-app
title: ഒരു പുതിയ React App ഉണ്ടാക്കാം
permalink: docs/create-a-new-react-app.html
redirect_from:
  - "docs/add-react-to-a-new-app.html"
prev: add-react-to-a-website.html
next: cdn-links.html
---

ഏറ്റവും മികച്ച ഡെവലപ്പർ എക്സ്പീരിയൻസിനും യൂസർ എക്സ്പീരിയൻസിനും വേണ്ടി ഇന്റഗ്രേറ്റഡ് ആയിട്ടുള്ള ഒരു Toolchain ഉപയോഗിക്കാം.

താഴെ പറയുന്ന കാര്യങ്ങൾ എളുപ്പമാക്കാൻ സഹായിക്കുന്ന ചില പ്രമുഖ Toolchain-നുകളെ കുറിച്ചാണ് ഈ പേജിൽ പ്രതിപാദിച്ചിരിക്കുന്നത്.

* ഒരുപാട് ഫയലുകളും Component-കളുമായി കൂട്ടിച്ചേർത്തു application വലുതാക്കിയെടുക്കാൻ
* npm-ഇൽ നിന്നും ലഭ്യമാകുന്ന 3rd party ലൈബ്രറികൾ ഉപയോഗിക്കാൻ
* സാധാരണയായി വരുത്തുന്ന തെറ്റുകൾ നേരത്തത്തെ തിരിച്ചറിയാൻ
* ഡെവലപ്മെന്റ് സമയത്ത് CSS-ലും JS-ലും വരുത്തുന്ന മാറ്റങ്ങൾ തത്സമയം വീക്ഷിക്കാൻ
* പ്രൊഡക്ഷൻ സാഹചര്യത്തിനനുസൃതമായി ഔട്ട്പുട്ട് optimize ചെയ്തെടുക്കാൻ.

ഈ പേജിൽ പറയുന്ന Toolchain-നുകൾ **ഉപയോഗിക്കാൻ യാതൊരു വിധ configuration-ന്റെയും ആവശ്യമില്ല**.

## നിങ്ങൾക്ക് ഒരു Toolchain ആവശ്യമായെന്നു തന്നെ വരില്ല. {#you-might-not-need-a-toolchain}

മുകളിൽ പ്രതിപാദിച്ചിരിക്കുന്ന വിഷയങ്ങൾ നിങ്ങൾക്ക് ഒരു പ്രശ്നമായി തോന്നിയിട്ടില്ലെങ്കിലോ അല്ലെങ്കിൽ JavaScript ടൂളുകൾ ഉപയോഗിക്കാൻ നിങ്ങൾ പ്രാപ്തരായിട്ടില്ലെങ്കിലോ നിങ്ങൾക്ക് [React ഒരു plain `<script>` ടാഗ് ആയി HTML പേജിൽ](/docs/add-react-to-a-website.html) ഉപയോഗിക്കാവുന്നതാണ്, അതിനോടൊപ്പം [വേണമെങ്കിൽ JSX](/docs/add-react-to-a-website.html#optional-try-react-with-jsx)-ഉം ഉപയോഗിക്കാം.

**നിലവിലുള്ള ഒരു വെബ്‌സൈറ്റിൽ React കൂട്ടിച്ചേർക്കുന്നതിനുള്ള ഏറ്റവും എളുപ്പമായ മാർഗ്ഗമാണിത്**. നിങ്ങൾക്ക് മറ്റൊരു വലിയ Toolchain ഉപകാരപ്രദമായി തോന്നുകയാണെങ്കിൽ അത് ഉപയോഗിക്കാവുന്നതാണ്!

## ശുപാർശ ചെയ്യുന്ന Toolchain-കൾ {#recommended-toolchains}

React ടീം പ്രധാനമായി ശുപാർശ ചെയ്യുന്നത് ഈ toolchain-കളാണ്:

- നിങ്ങൾ **React പഠിക്കുയാണെങ്കിലോ** അല്ലെങ്കിൽ **ഒരു പുതിയ React app നിർമ്മിക്കുകയാണെങ്കിലോ** [Create React App](#create-react-app) ഉപയോഗിക്കാം.
- **Node.js ഉപയോഗിച്ച് server render ചെയ്യുന്ന വെബ്‌സൈറ്റ്** ആണ് ഉണ്ടാക്കുന്നതെങ്കിൽ [Next.js](#nextjs) പരീക്ഷിച്ചു നോക്കാം.
- **static വെബ്‌സൈറ്റ്** ആണ് നിര്മിക്കുന്നതെങ്കിൽ [Gatsby](#gatsby) പരീക്ഷിച്ചു നോക്കാവുന്നതാണ്.
- നിങ്ങൾ ഒരു **component ലൈബ്രറിയോ** അല്ലെങ്കിൽ നിലവിലുള്ള ഒരു കോഡ്ബേസ് വികസിപ്പിച്ചെടുക്കാൻ ശ്രമിക്കുകയോ ആണെങ്കിൽ, [കൂടുതൽ Flexible ആയിട്ടുള്ള Toolchains](#more-flexible-toolchains) നോക്കാവുന്നതാണ്.

### Create React App {#create-react-app}

**React പഠിക്കുന്നതിനും** **ഒരു [single-page](/docs/glossary.html#single-page-application) React App** മികച്ച രീതിയിൽ ഉണ്ടാക്കിയെടുക്കുന്നതിനുള്ള ഏറ്റവും സുഖകരമായ സാഹചര്യം സൃഷ്ടിക്കുന്ന toolchain ആണ് [Create React App](https://github.com/facebookincubator/create-react-app).

<<<<<<< HEAD
<<<<<<< HEAD
ഇത് നിങ്ങൾക്ക് വേണ്ടി ഏറ്റവും പുതിയ JavaScript ഫീച്ചറുകൾ അടങ്ങിയ  മികച്ച ഒരു ഡെവലപ്പ്മെന്റ് സാഹചര്യം ഒരുക്കിത്തരികയും പ്രൊഡക്ഷനു വേണ്ടി നിങ്ങളുടെ app-നെ optimized ആക്കുകയും ചെയ്യുന്നു. ഇതിനായി നിങ്ങളുടെ കമ്പ്യൂട്ടറിൽ Node-ന്റെ 8.10-നേക്കാൾ ഉയർന്ന പതിപ്പും npm-ന്റെ 5.6-നേക്കാൾ ഉയർന്ന പതിപ്പും ഉണ്ടായിരിക്കണം. ഒരു പ്രൊജക്റ്റ് നിർമ്മിക്കുന്നതിനായി താഴെയുള്ള കമാൻഡ് റൺ ചെയ്യുക:
=======
It sets up your development environment so that you can use the latest JavaScript features, provides a nice developer experience, and optimizes your app for production. You’ll need to have [Node >= 8.10 and npm >= 5.6](https://nodejs.org/en/) on your machine. To create a project, run:
>>>>>>> bc91fe4101420f98454a59ac34c1cf1d4d4f4476
=======
It sets up your development environment so that you can use the latest JavaScript features, provides a nice developer experience, and optimizes your app for production. You’ll need to have [Node >= 14.0.0 and npm >= 5.6](https://nodejs.org/en/) on your machine. To create a project, run:
>>>>>>> e21b37c8cc8b4e308015ea87659f13aa26bd6356

```bash
npx create-react-app my-app
cd my-app
npm start
```

>കുറിപ്പ്
>
>`npx` എന്നത് ടൈപ്പ് ചെയ്തപ്പോൾ തെറ്റിയതല്ല -- അത് [npm 5.2-നു മുകളിൽ ഉള്ള പതിപ്പുകളോടൊപ്പം വരുന്ന ഒരു പാക്കേജ് റണ്ണർ ടൂൾ](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) ആണ്.

Create React App ഒരിക്കലും backend ലോജിക്കുകളോ ഡാറ്റാബേസുകളോ കൈകാര്യം ചെയ്യില്ല; ഇത് ഒരു frontend build pipeline മാത്രം ഉണ്ടാക്കുന്നതിനാൽ നിങ്ങൾക്ക് ഇഷ്ടമുള്ള backend-നോടോപ്പം ഉപയോഗിക്കാവുന്നതാണ്. അടിസ്ഥാനപരമായി ഇത് ഉപയോഗിച്ചിരിക്കുന്നത് [Babel](https://babeljs.io/)-ഉം [webpack](https://webpack.js.org/)-ഉം ആണ്. എന്നാൽ നിങ്ങൾ അതിനെ കുറിച്ചെല്ലാം അറിഞ്ഞിരിക്കണം എന്ന് നിർബന്ധമില്ല.

നിങ്ങൾ പ്രൊഡക്ഷനിലേക്ക് ഡിപ്ലോയ് ചെയ്യാൻ തയ്യാറാകുമ്പോൾ `npm run build` എന്ന കമാൻഡ് റൺ ചെയ്‌താൽ `build` ഫോൾഡറിനകത്ത് നിങ്ങളുടെ app-ന്റെ ഏറ്റവും optimize ആയിട്ടുള്ള ഒരു ബിൽഡ് ഉണ്ടായി വരുന്നതാണ്. നിങ്ങൾക്ക് Create React App-നെ കുറിച്ച് കൂടുതൽ മനസ്സിലാക്കാൻ [അതിന്റെ README](https://github.com/facebookincubator/create-react-app#create-react-app--) യോ [യൂസർ ഗൈഡോ](https://facebook.github.io/create-react-app/) നോക്കാവുന്നതാണ്.

### Next.js {#nextjs}

React ഉപയോഗിച്ച്‌ **static ആയിട്ടുള്ളതും server render ചെയ്യുന്നതുമായ application**-കൾ നിർമ്മിക്കുന്നതിനുള്ള ഏറ്റവും പപ്രശസ്തവും അമിതഭാരമില്ലാത്തതുമായ ഒരു ലൈബ്രറിയാണ്  [Next.js](https://nextjs.org/). **സ്റ്റൈൽ ചെയ്യുന്നതിനും route ചെയ്യുന്നതിനുമുള്ള ഉപാധികൾ** അതിനകത്തു തന്നെ നിലവിലുണ്ട്. [Node.js](https://nodejs.org/)-നെയാണ് നിങ്ങളുടെ സെർവർ ആയി ഇത് പ്രതീക്ഷിക്കുന്നത്.

Next.js നിങ്ങൾക്ക് [അതിന്റെ ഒഫിഷ്യൽ ഗൈഡിൽ](https://nextjs.org/learn/) നിന്നും പഠിച്ചെടുക്കാം.

### Gatsby {#gatsby}

React ഉപയോഗിച്ച് **static വെബ്‌സൈറ്റുകൾ** നിർമ്മിക്കുന്നതിനുള്ള ഏറ്റവും മികച്ച ഉപാധിയാണ് [Gatsby](https://www.gatsbyjs.org/). ഇതിൽ നിങ്ങൾ React components ആണ് ഉപയോഗിക്കുന്നതെങ്കിലും വേഗമേറിയ ലോഡിങ്ങ് ഉറപ്പു വരുത്തുന്ന രീതിയിൽ pre-render ചെയ്ത HTML-ഉം CSS-ഉം ആയിരിക്കും ഇതിന്റെ ഔട്ട്പുട്ട്.

[ഒഫിഷ്യൽ ഗൈഡി](https://www.gatsbyjs.org/docs/)ൽ നിന്നും [gallery of starter kit](https://www.gatsbyjs.org/docs/gatsby-starters/)-ൽ നിന്നും നിങ്ങൾക്ക് Gatsby പഠിച്ചെടുക്കാം.

### കൂടുതൽ Flexible ആയിട്ടുള്ള Toolchains {#more-flexible-toolchains}

താഴെ പറയുന്ന toolchain-കൾ കൂടുതൽ flexibility-യും രീതികളും നൽകുന്നവയാണ്. കൂടുതൽ പരിജ്ഞാനമുള്ളവർക്കേ ഞങ്ങൾ ഇത് ശുപാർശ ചെയ്യുന്നുള്ളൂ:

- **[Neutrino](https://neutrinojs.org/)**: ഇതിൽ [webpack](https://webpack.js.org/)-ന്റെ കഴിവുകൾ preset-കളുടെ ലാളിത്യവുമായി കൂട്ടിച്ചേർത്തു [React app](https://neutrinojs.org/packages/react/)കൾക്കും [React component](https://neutrinojs.org/packages/react-components/)-കൾക്കും ചേർന്ന preset-കൾ ഉൾക്കൊള്ളിച്ചിരിക്കുന്നു.

- **[nwb](https://github.com/insin/nwb)**: ഇത് [React component-കൾ npm-ൽ പ്രസിദ്ധീകരിക്കുന്നതിനും](https://github.com/insin/nwb/blob/master/docs/guides/ReactComponents.md#developing-react-components-and-libraries-with-nwb), [React app-കൾ ഉണ്ടാക്കുന്നതിനും](https://github.com/insin/nwb/blob/master/docs/guides/ReactApps.md#developing-react-apps-with-nwb) ഉള്ള ഒരു മികച്ച ഉപാധിയാണ്.

- **[Nx](https://nx.dev/react)** is a toolkit for full-stack monorepo development, with built-in support for React, Next.js, [Express](https://expressjs.com/), and more.

- **[Parcel](https://parceljs.org/)** is a fast, zero configuration web application bundler that [works with React](https://parceljs.org/recipes/react/).

- **[Razzle](https://github.com/jaredpalmer/razzle)**: ഇത് Next.js-നേക്കാൾ flexibility വാഗ്‌ദാനം ചെയ്യുന്ന configuration ആവശ്യമില്ലാത്ത server-rendering framework ആണ്.

## തുടക്കം മുതൽ ഒരു toolchain ഉണ്ടാക്കിയെടുക്കൽ {#creating-a-toolchain-from-scratch}

ഒരു JavaScript ബിൽഡ് toolchain-ഇൽ സാധാരണയായി ഉണ്ടാകുന്നത്:

* [Yarn](https://yarnpkg.com/) അല്ലെങ്കിൽ [npm](https://www.npmjs.com/) പോലെ ഒരു **package manager**. മറ്റുള്ളവർ ഉണ്ടാക്കി വെച്ചിട്ടുള്ള package-കൾ എളുപ്പത്തിൽ ഇൻസ്റ്റാൾ ചെയ്യാനും അപ്ഡേറ്റ് ചെയ്യാനും ഇത് സഹായിക്കുന്നു.

* [webpack](https://webpack.js.org/) അല്ലെങ്കിൽ [Parcel](https://parceljs.org/) പോലെ ഒരു **bundler**. ചെറിയ ഭാഗങ്ങൾ ആയി കോഡ് എഴുതിയ ശേഷം ലോഡിങ്ങ് സമയം പരമാവധി കുറവായ രീതിയിൽ അവയെ ഒന്നിച്ചാക്കാൻ ഇത് സഹായിക്കുന്നു.

* [Babel](https://babeljs.io/) പോലൊരു **compiler**. പഴയ ബ്രൗസറിലും ഓടുന്ന രീതിയിൽ പുതിയ JavaScript കോഡ് എഴുതാൻ ഇത് നിങ്ങളെ സഹായിക്കുന്നു.

നിങ്ങൾക്ക് സ്വന്തമായി ഒരു JavaScript toolchain ഉണ്ടാക്കാൻ താല്പര്യമുണ്ടെങ്കിൽ [ഈ ഗൈഡ് നോക്കാവുന്നതാണ്](https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658), അതിൽ Create React App-ന്റെ പ്രവർത്തികൾ പുനരാവിഷ്കരിക്കാൻ ശ്രമിച്ചിട്ടുണ്ട്.

നിങ്ങൾ സ്വന്തമായി ഉണ്ടാക്കുന്ന toolchain [പ്രൊഡക്ഷനുതകുന്ന രീതിയിൽ കൃത്യമായാണ് വികസിപ്പിച്ചെടുത്തതെന്നു](/docs/optimizing-performance.html#use-the-production-build) ഉറപ്പു വരുത്തുക.
