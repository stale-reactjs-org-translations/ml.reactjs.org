---
id: cdn-links
title: CDN ലിങ്കുകൾ
permalink: docs/cdn-links.html
prev: create-a-new-react-app.html
next: release-channels.html
---


React, ReactDOM എന്നിവ രണ്ടും ഒരു CDN വഴി ലഭ്യമാണ്.

```html
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
```

മുകളിലുള്ള പതിപ്പുകൾ ‍ഡെവലെപ്പ്മെന്റിന് മാത്രമുള്ളതാണ്, മാത്രമല്ല പ്രൊഡക്ഷന്  അനുയോജ്യവുമല്ല. Reactന്റെ ചെറുതും ഒപ്റ്റിമൈസ് ചെയ്തതുമായ പതിപ്പുകൾ ഇവിടെ ലഭ്യമാണ്:

```html
<script crossorigin src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
```

<<<<<<< HEAD
`React`,` react-dom` എന്നിവയുടെ നിർദ്ദിഷ്ട പതിപ്പ് ലോഡുചെയ്യാൻ, പതിപ്പ് നമ്പറിനൊപ്പം `16` മാറ്റിസ്ഥാപിക്കുക.
=======
To load a specific version of `react` and `react-dom`, replace `18` with the version number.
>>>>>>> f67fa22cc1faee261f9e22449d90323e26174e8e

###`crossorigin` ആട്രിബ്യൂട്ട് എന്തിനുവേണ്ടി? {#why-the-crossorigin-attribute}


നിങ്ങൾ ഒരു CDN- ൽ നിന്ന് React സേവിക്കുകയാണെങ്കിൽ, [`crossorigin`](https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_settings_attributes) ആട്രിബ്യൂട്ട് സെറ്റ് ചെയ്യാൻ ഞങ്ങൾ ശുപാർശ ചെയ്യുന്നു

```html
<script crossorigin src="..."></script>
```

നിങ്ങൾ ഉപയോഗിക്കുന്ന CDN -ൽ `Access-Control-Allow-Origin: *` HTTP header  സെറ്റ് ചെയ്യാൻ  ശുപാർശ ചെയ്യുന്നു:

![Access-Control-Allow-Origin: *](../images/docs/cdn-cors-header.png)

ഇത് React 16 ലും അതിനുശേഷമുള്ളതിലും മികച്ച [എറർ ഹാൻഡ്‌ലിംഗ് എക്സ്പീരിയൻസ്](/blog/2017/07/26/error-handling-in-react-16.html) പ്രാപ്തമാക്കുന്നു.
