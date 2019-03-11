---
id: hooks-intro
title: Hooks പരിചയപ്പെടുത്തുന്നു
permalink: docs/hooks-intro.html
next: hooks-overview.html
---

React 16.8 ലെ പുതിയതായി ചേർക്കപ്പെട്ട ഫീച്ചർ ആണ് *Hooks*. ഇത് ഉപയോഗിച്ച് നിങ്ങൾക്കു state ഉം മറ്റു ഫീച്ചർ class ഇല്ലാതെ ഉപയോഗിക്കാൻ ആകും.

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
>React 16.8.0 ൽ ആണ് hooks ലൈബ്രറിയിൽ ചേർക്കുന്നത്. നിങ്ങൾ hooks ഉപയോഗിക്കുമ്പോൾ React DOM ഉൾപ്പടെ അലാ ലൈബ്രറികളും അപ്ഗ്രേഡ് ചെയാൻ മറക്കരുത്. React Native അടുത്ത റിലീസ് മുതൽ hooks ഉൾപ്പെടുത്തും.

## ദൃശ്യം {#video-introduction}

React Conference 2018 ൽ വച്ച് സോഫി അൽപ്പർട്ടും ഡാൻ അബ്രമോവും കൂടി ആണ് hooks ആദ്യം ആയി അവതരിപ്പിച്ചത്. പിന്നീട് റയാൻ ഫ്ലോറെൻസ് hooks ഉപയോഗിച്ച് ഒരു അപ്ലിക്കേഷൻ എഴുതി കാണിക്കുകയും ചെയ്തു. അതിന്റെ ദൃശ്യങ്ങൾ ചുവടെ ചേർക്കുന്നു.

<br>

<iframe width="650" height="366" src="//www.youtube.com/embed/dpw9EHDh2bM" frameborder="0" allowfullscreen></iframe>

## ബ്രേക്കിംഗ് മാറ്റങ്ങൾ ഇല്ല {#no-breaking-changes}

മുൻപോട്ടു പോകുന്നതിനു മുൻപ് അറിഞ്ഞിരിക്കേണ്ട കുറച്ചു കാര്യങ്ങൾ:

* **Completely opt-in.** ഇപ്പോൾ നിങ്ങൾ എഴുതിയിട്ടുള്ള components ഒന്നും മാറ്റാതെ തന്നേ നിങ്ങൾക്കു Hooks ഉപയോഗിച്ചു കോഡ് ചെയ്തു തുടങ്ങാവുന്നത് ആണ്. ഇപ്പോൾ പഠിക്കേണ്ട എന്ന് തോന്നുന്നുണ്ടെങ്കിൽ വേണ്ട എന്ന് വക്കാം.
* **100% backwards-compatible.**  ഇപ്പോൾ ഉള്ള code ഇനെ പൊട്ടിക്കുന്ന മാറ്റങ്ങൾ ഒന്നും hooks കൊണ്ട് വരുന്നില്ല.
* **ഇപ്പോൾ ലഭ്യമാണ്** React 16.8.0 മുതൽ hooks ലഭ്യം ആണ്.

**class React ൽ നിന്നും ഒഴിവാകുകയല്ല.** ക്രമേണ എങ്ങനെ hooks ഉപയോഗിച്ചു തുടങ്ങാം എന്ന് [ചുവടെ](#gradual-adoption-strategy) ചേർക്കുന്നു.

**Hooks don't replace your knowledge of React concepts.** Instead, Hooks provide a more direct API to the React concepts you already know: props, state, context, refs, and lifecycle. As we will show later, Hooks also offer a new powerful way to combine them.

**If you just want to start learning Hooks, feel free to [jump directly to the next page!](/docs/hooks-overview.html)** You can also keep reading this page to learn more about why we're adding Hooks, and how we're going to start using them without rewriting our applications.

## Motivation {#motivation}

Hooks solve a wide variety of seemingly unconnected problems in React that we've encountered over five years of writing and maintaining tens of thousands of components. Whether you're learning React, use it daily, or even prefer a different library with a similar component model, you might recognize some of these problems.

### It's hard to reuse stateful logic between components {#its-hard-to-reuse-stateful-logic-between-components}

React doesn't offer a way to "attach" reusable behavior to a component (for example, connecting it to a store). If you've worked with React for a while, you may be familiar with patterns like [render props](/docs/render-props.html) and [higher-order components](/docs/higher-order-components.html) that try to solve this. But these patterns require you to restructure your components when you use them, which can be cumbersome and make code harder to follow. If you look at a typical React application in React DevTools, you will likely find a "wrapper hell" of components surrounded by layers of providers, consumers, higher-order components, render props, and other abstractions. While we could [filter them out in DevTools](https://github.com/facebook/react-devtools/pull/503), this points to a deeper underlying problem: React needs a better primitive for sharing stateful logic.

With Hooks, you can extract stateful logic from a component so it can be tested independently and reused. **Hooks allow you to reuse stateful logic without changing your component hierarchy.** This makes it easy to share Hooks among many components or with the community.

We'll discuss this more in [Building Your Own Hooks](/docs/hooks-custom.html).

### Complex components become hard to understand {#complex-components-become-hard-to-understand}

We've often had to maintain components that started out simple but grew into an unmanageable mess of stateful logic and side effects. Each lifecycle method often contains a mix of unrelated logic. For example, components might perform some data fetching in `componentDidMount` and `componentDidUpdate`. However, the same `componentDidMount` method might also contain some unrelated logic that sets up event listeners, with cleanup performed in `componentWillUnmount`. Mutually related code that changes together gets split apart, but completely unrelated code ends up combined in a single method. This makes it too easy to introduce bugs and inconsistencies.

In many cases it's not possible to break these components into smaller ones because the stateful logic is all over the place. It's also difficult to test them. This is one of the reasons many people prefer to combine React with a separate state management library. However, that often introduces too much abstraction, requires you to jump between different files, and makes reusing components more difficult.

To solve this, **Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data)**, rather than forcing a split based on lifecycle methods. You may also opt into managing the component's local state with a reducer to make it more predictable.

We'll discuss this more in [Using the Effect Hook](/docs/hooks-effect.html#tip-use-multiple-effects-to-separate-concerns).

### Classes confuse both people and machines {#classes-confuse-both-people-and-machines}

In addition to making code reuse and code organization more difficult, we've found that classes can be a large barrier to learning React. You have to understand how `this` works in JavaScript, which is very different from how it works in most languages. You have to remember to bind the event handlers. Without unstable [syntax proposals](https://babeljs.io/docs/en/babel-plugin-transform-class-properties/), the code is very verbose. People can understand props, state, and top-down data flow perfectly well but still struggle with classes. The distinction between function and class components in React and when to use each one leads to disagreements even between experienced React developers.

Additionally, React has been out for about five years, and we want to make sure it stays relevant in the next five years. As [Svelte](https://svelte.technology/), [Angular](https://angular.io/), [Glimmer](https://glimmerjs.com/), and others show, [ahead-of-time compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) of components has a lot of future potential. Especially if it's not limited to templates. Recently, we've been experimenting with [component folding](https://github.com/facebook/react/issues/7323) using [Prepack](https://prepack.io/), and we've seen promising early results. However, we found that class components can encourage unintentional patterns that make these optimizations fall back to a slower path. Classes present issues for today's tools, too. For example, classes don't minify very well, and they make hot reloading flaky and unreliable. We want to present an API that makes it more likely for code to stay on the optimizable path.

To solve these problems, **Hooks let you use more of React's features without classes.** Conceptually, React components have always been closer to functions. Hooks embrace functions, but without sacrificing the practical spirit of React. Hooks provide access to imperative escape hatches and don't require you to learn complex functional or reactive programming techniques.

>Examples
>
>[Hooks at a Glance](/docs/hooks-overview.html) is a good place to start learning Hooks.

## Gradual Adoption Strategy {#gradual-adoption-strategy}

>**TLDR: There are no plans to remove classes from React.**

We know that React developers are focused on shipping products and don't have time to look into every new API that's being released. Hooks are very new, and it might be better to wait for more examples and tutorials before considering learning or adopting them.

We also understand that the bar for adding a new primitive to React is extremely high. For curious readers, we have prepared a [detailed RFC](https://github.com/reactjs/rfcs/pull/68) that dives into motivation with more details, and provides extra perspective on the specific design decisions and related prior art.

**Crucially, Hooks work side-by-side with existing code so you can adopt them gradually.** There is no rush to migrate to Hooks. We recommend avoiding any "big rewrites", especially for existing, complex class components. It takes a bit of a mindshift to start "thinking in Hooks". In our experience, it's best to practice using Hooks in new and non-critical components first, and ensure that everybody on your team feels comfortable with them. After you give Hooks a try, please feel free to [send us feedback](https://github.com/facebook/react/issues/new), positive or negative.

We intend for Hooks to cover all existing use cases for classes, but **we will keep supporting class components for the foreseeable future.** At Facebook, we have tens of thousands of components written as classes, and we have absolutely no plans to rewrite them. Instead, we are starting to use Hooks in the new code side by side with classes.

## പതിവ് ചോദ്യങ്ങൾ {#frequently-asked-questions}

ഞങ്ങൾ hooks ഇനെ കുറിച്ച് ഉള്ള [പതിവ് ചോദ്യങ്ങളുടെ പട്ടിക](/docs/hooks-faq.html) തയാറാക്കിയിട്ടുണ്ട്.

## Next Steps {#next-steps}

By the end of this page, you should have a rough idea of what problems Hooks are solving, but many details are probably unclear. Don't worry! **Let's now go to [the next page](/docs/hooks-overview.html) where we start learning about Hooks by example.**
