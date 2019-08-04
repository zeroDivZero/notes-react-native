# VS REACT

In render phase, React takes markup returned from component's **render** method and renders it directly to page.

Instead of rendering to browser's DOM, RN invokes Obj-C APIs to render to iOS components, or Java APIs for Android. This also sets RN apart from other cross-platform frameworks, which often render web-based views.

React/RN has *connector* layer to interface with host platform's API to translate markup into native UI elements (for Web browser, no translation necessary). Can support any platform if connector implemented.

## Bridge

Specifically, RN uses **bridge** to establish bidirectional, async communication between JS and native realms.

Behaves like *message queue*. First service pushes commands to queue, other one executes them when possible. Ex: JS realm sends async JSON message describing views that must be created, and when native side ready, it creates them.

Another benefit of async: non-blocking, so RN doesn't run on main thread, allowing smooth view management (~6O fps).

Built in C/C++, so it runs on many platforms. Embeds Apple's [JavaScriptCore](https://developer.apple.com/documentation/javascriptcore) framework (to evaluate JS within Swift, Obj-C, and C-based apps; part of open-source **WebKit**), which exposes JS VM API. On iOS side Obj-C is just extension of C, so bridge can talk native directly. On Android side requires **Java Native Interface (JNI)**.
