---
id: release-channels
title: റിലീസ് ചാനലുകൾ
permalink: docs/release-channels.html
layout: docs
category: installation
prev: cdn-links.html
next: hello-world.html
---

ബഗ്ഗ്‌ റിപ്പോർട്ടുകൾ ഫയൽ ചെയ്യുന്നതിനും pull request-കൾ ഇടുന്നതിനും [RFC-കൾ സബ്മിറ്റ് ചെയ്യുന്നതിനും](https://github.com/reactjs/rfcs) വേണ്ടി സമ്പന്നമായ ഒരു ഓപ്പൺസോഴ്സ് കമ്മ്യൂണിറ്റിയെയാണ് React ആശ്രയിച്ചിരിക്കുന്നത്. കൂടുതൽ പ്രതികരണങ്ങൾ ലഭിക്കുന്നതിനായി റിലീസ് ചെയ്യാത്ത ഫീച്ചറുകൾ അടങ്ങിയ ചില ബിൽഡുകൾ ഞങ്ങൾ പങ്കുവെക്കാറുണ്ട്.

> ഈ ഡോക്യുമെന്റ് പ്രധാനമായും framework-കൾ, library-കൾ, അല്ലെങ്കിൽ developer tooling എന്നിവ നിർമ്മിക്കുന്ന ഡെവലപ്പർമാർക്ക് അനുയോജ്യമായതാണ്. user-facing applications ഉണ്ടാക്കുന്നത്തിനു മാത്രം React ഉപയോഗിക്കുന്ന ഡെവലപ്പർമാർ ഞങ്ങളുടെ prerelease ചാനലുകളെ കുറിച്ച് ആശങ്കപ്പെടേണ്ടതില്ല.

React-ന്റെ ഓരോ റിലീസ് ചാനലുകളും ഡിസൈൻ ചെയ്തിരിക്കുന്നത് വ്യത്യസ്തങ്ങളായ use case-കൾക്ക് വേണ്ടിയാണ്:

<<<<<<< HEAD
- [**Latest**](#latest-channel) ചാനൽ ഏറ്റവും സ്ഥിരതയുള്ള semver React റിലീസുകൾക്ക് വേണ്ടിയുള്ളതാണ്. npm-ഇത് നിന്നും React ഇൻസ്റ്റാൾ ചെയ്യുമ്പോൾ നിങ്ങൾക്ക് ലഭിക്കുന്നത് ഇതായിരിക്കും. നിങ്ങൾ ഇപ്പോൾ ഉപയോഗിച്ച് കൊണ്ടിരിക്കുന്നത് ഈ ചാനൽ ആണ്. **user-facing ആയിട്ടുള്ള എല്ലാ React application-കൾക്കും വേണ്ടി ഇതുപയോഗിക്കാം.**
- [**Next**](#next-channel) ചാനൽ React സോഴ്സ് കോഡ് repository-യുടെ master branch-നെ പിന്തുടരുന്നതാണ്. അടുത്ത ഒരു minor semver റിലീസിനായി പരീക്ഷിക്കാൻ വെച്ചിരിക്കുന്ന ഒന്നായി ഇതിനെ കണക്കാക്കാം. Third party project-കളും React-ഉം തമ്മിലുള്ള integration testing-നായി ഇത് ഉപയോഗിക്കാവുന്നതാണ്.
- [**Experimental**](#experimental-channel) ചാനലിൽ സ്ഥിരതയുള്ള റിലീസിൽ ലഭ്യമല്ലാത്ത പരീക്ഷണാടിസ്ഥാനത്തിൽ ഉള്ള API-കളും ഫീച്ചറുകളും ഉൾക്കൊള്ളിച്ചിരിക്കുന്നു. ഇത് master branch-നെ പിന്തുടരുന്നതാണെങ്കിൽ കൂടി കൂടുതൽ ഫീച്ചർ ഫ്ലാഗുകൾ ഇതിൽ ഓൺ ആയിരിക്കും. വരാനിരിക്കുന്ന ഫീച്ചറുകൾ റിലീസിന് മുൻപ് പരീക്ഷിക്കുന്നതിനായി ഇതുപയോഗിക്കാം.

എല്ലാ റിലീസുകളും npm-ഇൽ പ്രസിദ്ധീകരിക്കുമെങ്കിലും [semantic versioning](/docs/faq-versioning.html) ഉപയോഗിക്കുന്നത് Latest-ൽ മാത്രമായിരിക്കും. Prerelease-കൾ(Next, Experimental എന്നീ ചാനലുകളിൽ) അവയുടെ ഉള്ളടക്കത്തിൽ നിന്നുള്ള ഒരു hash ആയിരിക്കും version ആയി ഉപയോഗിക്കുന്നത്. ഉദാഹരണത്തിന്: `0.0.0-1022ee0ec` എന്നത് Next-ലും `0.0.0-experimental-1022ee0ec` എന്നത് Experimental-ലും.
=======
- [**Latest**](#latest-channel) is for stable, semver React releases. It's what you get when you install React from npm. This is the channel you're already using today. **Use this for all user-facing React applications.**
- [**Next**](#next-channel) tracks the main branch of the React source code repository. Think of these as release candidates for the next minor semver release. Use this for integration testing between React and third party projects.
- [**Experimental**](#experimental-channel) includes experimental APIs and features that aren't available in the stable releases. These also track the main branch, but with additional feature flags turned on. Use this to try out upcoming features before they are released.

All releases are published to npm, but only Latest uses [semantic versioning](/docs/faq-versioning.html). Prereleases (those in the Next and Experimental channels) have versions generated from a hash of their contents and the commit date, e.g. `0.0.0-68053d940-20210623` for Next and `0.0.0-experimental-68053d940-20210623` for Experimental.
>>>>>>> 4fab3d31469ab7a53dbf8b50cab5d57880a0c035

**user-facing application-കൾക്ക് വേണ്ടി ഞങ്ങൾ ഔദ്യോഗികമായി പിന്തുണക്കുന്ന ഏക ചാനൽ Latest ആണ്**. Next-ന്റെയും Experimental-ന്റെയും റിലീസുകൾ ടെസ്റ്റിംഗ് ആവശ്യങ്ങൾക്കു വേണ്ടിയുള്ളതാണ്. ഓരോ റിലീസുകളിലും ഇവയുടെ behavior മാറില്ല എന്നതിന് യാതൊരുവിധ ഗ്യാരണ്ടിയും ഞങ്ങൾ നൽകുന്നില്ല. Latest-ൽ നിന്നും ഞങ്ങൾ ഇറക്കുന്ന റിലീസുകൾക്ക് ഉപയോഗിക്കുന്ന semver protocol ഇവ രണ്ടും പിന്തുടരുന്നില്ല.

സ്ഥിരതയുള്ള റിലീസുകൾക്ക് വേണ്ടി ഉപയോഗിക്കുന്ന അതേ registry തന്നെ prerelease-കൾ പ്രസിദ്ധീകരിക്കുന്നതിനും ഉപയോഗിക്കുന്നതിനാൽ [unpkg](https://unpkg.com)-യും [CodeSandbox](https://codesandbox.io)-ഉം പോലെ npm workflow സപ്പോർട്ട് ചെയ്യുന്ന നിരവധി ടൂളുകളുടെ സഹായം ഇതിലും ഉപയോഗപ്പെടുത്താം.

<<<<<<< HEAD
### Latest ചാനൽ {#latest-channel}
=======
### Latest Channel {#latest-channel}
>>>>>>> bbea52211971834d041e76871df8981066c42a3b

Latest ചാനൽ സ്ഥിരതയുള്ള React റിലീസുകൾക്ക് വേണ്ടി ഉപയോഗിക്കുന്നതാണ്. ഇത് npm-ലെ `latest` എന്ന ടാഗിനോട് ചേർന്നിരിക്കുന്നതായിരിക്കും. end-users-നു വേണ്ടി നിർമ്മിക്കുന്ന എല്ലാ React app-കൾക്കും വേണ്ടി നിർദ്ദേശിക്കുന്നത് ഈ ചാനൽ ആണ്.

**ഏത് ചാനൽ ഉപയോഗിക്കണം എന്ന് നിങ്ങൾക്ക് തീരുമാനിക്കാൻ കഴിയുന്നില്ലെങ്കിൽ Latest ഉപയോഗിക്കൂ.** നിങ്ങൾ ഒരു React ഡെവലപ്പർ ആണെങ്കിൽ ഇതായിരിക്കും നിങ്ങൾ ഉപയോഗിച്ച് കൊണ്ടിരിക്കുന്നത്.

Latest-ലേക്കുള്ള അപ്ഡേറ്റുകൾ വളരെയധികം സ്ഥിരതയാർജ്ജിച്ചതായിരിക്കും. ഇതിലെ പതിപ്പുകൾ semantic versioning scheme പിന്തുടരുന്നവയാണ്. സ്ഥിരതക്കും നിലവാരം ഉയർത്തുന്നതിനുമുള്ള പ്രതിജ്ഞാബദ്ധതയെ കുറിച്ച് ഞങ്ങളുടെ [versioning policy](/docs/faq-versioning.html)-യിൽ വായിക്കാവുന്നതാണ്.

<<<<<<< HEAD
### Next ചാനൽ {#next-channel}
=======
### Next Channel {#next-channel}
>>>>>>> bbea52211971834d041e76871df8981066c42a3b

<<<<<<< HEAD
React repository-യുടെ master branch-നെ പിന്തുടരുന്ന ഒരു prerelease ചാനൽ ആണ് Next ചാനൽ. Latest ചാനലിലേക്കുള്ള അടുത്ത release candidate ആയി Next ചാനലിലെ prerelease-കൾ ഉപയോഗിക്കുന്നു. Latest-ന്റെ ഇടക്കിടെ അപ്ഡേറ്റ് ചെയ്യുന്ന ഒരു superset ആയി Next-നെ കണക്കാക്കാവുന്നതാണ്.
=======
The Next channel is a prerelease channel that tracks the main branch of the React repository. We use prereleases in the Next channel as release candidates for the Latest channel. You can think of Next as a superset of Latest that is updated more frequently.
>>>>>>> 4fab3d31469ab7a53dbf8b50cab5d57880a0c035

Next-ന്റെ ഏറ്റവും അടുത്ത റിലീസും Latest-ന്റെ ഏറ്റവും അടുത്ത റിലീസും തമ്മിലുള്ള വ്യത്യാസങ്ങളുടെ തോത് ഏകദേശം രണ്ട് minor semver റിലീസുകൾക്ക് തുല്യമായിരിക്കും. എന്നാൽ പോലും **Next ചാനൽ semantic versioning അനുവർത്തിച്ചു കൊള്ളണം എന്നില്ല.** Next ചാനലിലെ അടുത്തടുത്തുള്ള രണ്ട് റിലീസുകൾക്കിടയിൽ breaking ആയിട്ടുള്ള മാറ്റങ്ങൾ നിങ്ങൾക്ക് പ്രതീക്ഷിക്കാവുന്നതാണ്.

**user-facing application-കളിൽ ഒരിക്കലും prerelease-കൾ ഉപയോഗിക്കരുത്.**

<<<<<<< HEAD
Next-ലെ റിലീസുകൾ npm-ഇൽ പ്രസിദ്ധീകരിക്കുന്നത് `next` എന്ന ടാഗോടു കൂടിയായിരിക്കും. ബിൽഡിന്റെ ഉള്ളടക്കത്തിൽ നിന്നും ഉണ്ടാക്കിയെടുക്കുന്ന ഒരു hash ആയിരിക്കും ഇതിന്റെ version, ഉദാഹരണം: `0.0.0-1022ee0ec`.
=======
Releases in Next are published with the `next` tag on npm. Versions are generated from a hash of the build's contents and the commit date, e.g. `0.0.0-68053d940-20210623`.
>>>>>>> 4fab3d31469ab7a53dbf8b50cab5d57880a0c035

<<<<<<< HEAD
#### Integration Testing-നു വേണ്ടിയുള്ള Next ചാനലിന്റെ ഉപയോഗം. {#using-the-next-channel-for-integration-testing}
=======
#### Using the Next Channel for Integration Testing {#using-the-next-channel-for-integration-testing}
>>>>>>> bbea52211971834d041e76871df8981066c42a3b

മറ്റു പ്രോജെക്ടുകളും React-ഉം തമ്മിലുള്ള integration testing സപ്പോർട്ട് ചെയ്യുന്നതിന് വേണ്ടിയാണ് Next ചാനൽ ഡിസൈൻ ചെയ്തിരിക്കുന്നത്.

React-ലെ എല്ലാ മാറ്റങ്ങളും പൊതുജനങ്ങൾക്കായി റിലീസ് ചെയ്യുന്നതിന് മുൻപ് ആഭ്യന്തരമായി സമഗ്രമായ testing-നു വിധേയമാക്കുന്നതാണ്. എന്നിരുന്നാലും അനേകായിരം configuration-കളിലും സാഹചര്യങ്ങളിലും React ecosystem ഉപയോഗിക്കുന്നതിനാൽ അവയോരോന്നിലും ഇത് ടെസ്റ്റ് ചെയ്യുക എന്നത് ഞങ്ങളെ കൊണ്ട് സാധ്യമല്ല.

നിങ്ങൾ ഒരു third party React framework, library, developer tool, അല്ലെങ്കിൽ അത്തരത്തിൽ ഉള്ള ഒരു infrastructure-type project-ന്റെ ഡെവലപ്പർ ആണെങ്കിൽ നിങ്ങളുടെ ഉപഭോക്താക്കൾക്കും React കമ്മ്യൂണിറ്റിക്കും വേണ്ടി React-ന്റെ സ്ഥിരത നിലനിർത്താൻ ഞങ്ങളെ സഹായിക്കാവുന്നതാണ്. ഇതിനായി നിങ്ങളുടെ test suite ആനുകാലികമായി റൺ ചെയ്‌താൽ മതിയാകും. നിങ്ങൾക്ക് താല്പര്യമുണ്ടെങ്കിൽ ഈ സ്റ്റെപ്പുകൾ പിന്തുടരാം.

- നിങ്ങൾക്ക് അനുയോജ്യമായ continuous integration platform ഉപയോഗിച്ച്‌ ഒരു cron job ഉണ്ടാക്കി വെക്കാം. [CircleCI](https://circleci.com/docs/2.0/triggers/#scheduled-builds)-യും [Travis CI](https://docs.travis-ci.com/user/cron-jobs/)-യും Cron job-കൾ സപ്പോർട്ട് ചെയ്യുന്നുണ്ട്.
- Cron Job-ഇൽ നിങ്ങളുടെ React പാക്കേജുകൾ npm-ലെ `next` ടാഗ് ഉപയോഗിക്കുന്ന Next ചാനലിലെ ഏറ്റവും പുതിയ React റിലീസിലേക്ക് അപ്ഡേറ്റ് ചെയ്യാം. npm cli ഉപയോക്കുന്നുവെങ്കിൽ:

  ```
  npm update react@next react-dom@next
  ```

  yarn ആണെങ്കിൽ:

  ```
  yarn upgrade react@next react-dom@next
  ```
- അപ്ഡേറ്റ് ചെയ്ത പാക്കേജുകളിൽ test suite റൺ ചെയ്യാം.
- എല്ലാം പാസ് ആകുകയാണെങ്കിൽ ഗംഭീരം. React-ന്റെ അടുത്ത minor റിലീസിലും നിങ്ങളുടെ പ്രോജെക്ട് വർക്ക് ചെയ്യുമെന്ന് നിങ്ങൾക്ക് പ്രതീക്ഷിക്കാം.
- അപ്രതീക്ഷിതമായി എന്തെങ്കിലും തകരുന്നുണ്ടെങ്കിൽ ദയവായി [ഒരു issue ഫയൽ ചെയ്തു](https://github.com/facebook/react/issues) ഞങ്ങളെ അറിയിക്കുക.

ഈ workflow ഉപയോഗിക്കുന്ന ഒരു പ്രോജെക്ട് ആണ് Next.js. (ശരിക്കും ഇതൊരു ദ്വയാര്‍ത്ഥ പ്രയോഗമല്ല!) അവരുടെ [CircleCI configuration](https://github.com/zeit/next.js/blob/c0a1c0f93966fe33edd93fb53e5fafb0dcd80a9e/.circleci/config.yml) സംശയനിവാരണത്തിനുള്ള ഒരു ഉദാഹരണമായി പരിശോധിക്കാവുന്നതാണ്.

<<<<<<< HEAD
### Experimental ചാനൽ {#experimental-channel}
=======
### Experimental Channel {#experimental-channel}
>>>>>>> bbea52211971834d041e76871df8981066c42a3b

<<<<<<< HEAD
Next പോലെ React repository-യുടെ master branch-നെ പിൻതുടരുന്ന ഒരു prerelease ചാനൽ ആണ് Experimental ചാനൽ. Experimental റിലീസിൽ, Next-ഇൽ നിന്നും വിഭിന്നമായി വിശാലമായി റിലീസ് ചെയ്യാൻ തയ്യാറായിട്ടില്ലാത്ത കൂടുതൽ ഫീച്ചറുകളും API-കളും ഉൾകൊള്ളുന്നു.
=======
Like Next, the Experimental channel is a prerelease channel that tracks the main branch of the React repository. Unlike Next, Experimental releases include additional features and APIs that are not ready for wider release.
>>>>>>> 4fab3d31469ab7a53dbf8b50cab5d57880a0c035

സാധാരണയായി, Next-ലെ ഒരു അപ്ഡേറ്റ് Experimental-ലെ അപ്ഡേറ്റിനെ അനുഗമിക്കുന്നതായിരിക്കും. അവ ഒരേ source revision അടിസ്ഥാനപ്പെടുത്തിയുള്ളതായിരിക്കും. എന്നാൽ അവ നിർമ്മിച്ചിരിക്കുന്നത് വ്യത്യസ്തമായ ഫീച്ചർ ഫ്ലാഗുകളുടെ കൂട്ടം ഉപയോഗിച്ചായിരിക്കും.

Experimental റിലീസുകൾ Next-ൽ നിന്നും Latest-ൽ നിന്നും ഗണ്യമായ മാറ്റങ്ങൾ ഉള്ളതായിരിക്കും. **user-facing application-കൾ ഉണ്ടാക്കാൻ ഒരിക്കലും Experimental റിലീസുകൾ ഉപയോഗിക്കരുത്.** Experimental ചാനലിലെ റിലീസുകൾക്കിടയിൽ breaking ആയിട്ടുള്ള മാറ്റങ്ങൾ നിങ്ങൾക്ക് പ്രതീക്ഷിക്കാവുന്നതാണ്.

<<<<<<< HEAD
Experimental-ലെ റിലീസുകൾ npm-ഇൽ പ്രസിദ്ധീകരിക്കുന്നത് `experimental` ടാഗോട് കൂടെയായിരിക്കും.  ബിൽഡിന്റെ ഉള്ളടക്കത്തിൽ നിന്നും ഉണ്ടാക്കിയെടുക്കുന്ന ഒരു hash ആയിരിക്കും ഇതിന്റെ version, ഉദാഹരണം:`0.0.0-experimental-1022ee0ec`.
=======
Releases in Experimental are published with the `experimental` tag on npm. Versions are generated from a hash of the build's contents and the commit date, e.g. `0.0.0-experimental-68053d940-20210623`.
>>>>>>> 4fab3d31469ab7a53dbf8b50cab5d57880a0c035

<<<<<<< HEAD
#### എന്താണ് Experimental റിലീസിലേക്ക് പോകുന്നത്? {#what-goes-into-an-experimental-release}
=======
#### What Goes Into an Experimental Release? {#what-goes-into-an-experimental-release}
>>>>>>> bbea52211971834d041e76871df8981066c42a3b

വിശാലമായ പൊതുജനങ്ങൾക്ക് റിലീസ് ചെയ്യാൻ തയ്യാറായിട്ടില്ലാത്തവയാണ് Experimental ഫീച്ചറുകൾ. അവ അന്തിമരൂപത്തിനു മുൻപായി വൻമാറ്റങ്ങൾക്ക് വിധേയമായേക്കാം. ചില പരീക്ഷണങ്ങൾ ഒരിക്കലും അന്തിമരൂപം പ്രാപിച്ചെന്നു വരില്ല -- നിർദ്ദിഷ്ട മാറ്റങ്ങളുടെ പ്രവർത്തനക്ഷമത പരിശോധിക്കുക എന്നതാണ് ഞങ്ങൾ പരീക്ഷണങ്ങളുണ്ടാക്കാനുള്ള കാരണം

ഉദാഹരണത്തിന്, ഞങ്ങൾ Hooks പ്രഖ്യാപിച്ച സമയത്ത് Experimental ചാനൽ നിലവിലുണ്ടായിരുന്നെങ്കിൽ, Latest-ൽ ലഭ്യമാക്കുന്നതിന് ആഴ്ചകൾക്ക് മുൻപേ Experimental ചാനലിൽ അവ റിലീസ് ചെയ്യുമായിരുന്നു.

Experimental-ൽ integration test-കൾ ഓടിക്കുക എന്നത് നിങ്ങൾക്ക് വിലപ്പെട്ടതായി തോന്നിയേക്കാം. അത് നിങ്ങളുടെ ഇഷ്ടത്തിന് വിട്ടു തന്നിരിക്കുന്നു. എന്നാൽ Experimental, Next-നേക്കാൾ സ്ഥിരത കുറഞ്ഞതാണെന്നു ഓർത്തിരിക്കുക. **Experimental റിലീസുകൾക്കിടയിൽ ഉള്ള സ്ഥിരതയെ പറ്റി യാതൊരുവിധ ഗ്യാരണ്ടിയും ഞങ്ങൾ നൽകുന്നില്ല.**

<<<<<<< HEAD
#### Experimental ഫീച്ചറുകളെ പറ്റി എനിക്കെങ്ങനെ കൂടുതൽ പഠിക്കാം? {#how-can-i-learn-more-about-experimental-features}
=======
#### How Can I Learn More About Experimental Features? {#how-can-i-learn-more-about-experimental-features}
>>>>>>> bbea52211971834d041e76871df8981066c42a3b

<<<<<<< HEAD
Experimental ഫീച്ചറുകൾ ഡോക്യുമെന്റ് ചെയ്യാനും അല്ലാതിരിക്കാനും സാധ്യതയുണ്ട്. സാധാരണയായി പരീക്ഷണങ്ങൾ ഡോക്യുമെന്റ് ചെയ്യുന്നത് അവ Next-ലേക്കോ സ്ഥിരതയുള്ളതിലേക്കോ കൂട്ടിച്ചേർക്കാൻ ആകുമ്പോൾ ആണ്.
=======
Experimental features may or may not be documented. Usually, experiments aren't documented until they are close to shipping in Next or Latest.
>>>>>>> c89c38241278804b48bf34b1d8d9ee0b9f1b6e8c

ഒരു ഫീച്ചർ ഡോക്യുമെന്റ് ചെയ്തിട്ടില്ലെങ്കിൽ അത് ഒരു [RFC](https://github.com/reactjs/rfcs)-യെ അനുഗമിക്കുന്നതായിരിക്കും.

പുതിയ പരീക്ഷണങ്ങൾ പ്രഖ്യാപിക്കാൻ ഞങ്ങൾ തയ്യാറാകുമ്പോൾ അവ [React blog](/blog)-ഇൽ പോസ്റ്റ് ചെയ്യുന്നതാണ്. അതിനർത്ഥം എല്ലാ പരീക്ഷണങ്ങളും ഞങ്ങൾ പരസ്യപ്പെടുത്തിക്കൊള്ളണം എന്നല്ല.

<<<<<<< HEAD
മാറ്റങ്ങളുടെ സമഗ്രമായ ലിസ്റ്റിനായി ഞങ്ങളുടെ public GitHub repository-യുടെ [history](https://github.com/facebook/react/commits/master) പരിശോധിക്കാവുന്നതാണ്.
=======
You can always refer to our public GitHub repository's [history](https://github.com/facebook/react/commits/main) for a comprehensive list of changes.
>>>>>>> 4fab3d31469ab7a53dbf8b50cab5d57880a0c035
