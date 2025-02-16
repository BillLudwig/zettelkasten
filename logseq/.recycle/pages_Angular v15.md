tags:: WebDev, Angular

- ## Big Changes
	- {{video https://www.youtube.com/watch?v=-n0WhqabSmc}}
	- [Standalone Components](https://angular.io/guide/standalone-components) are out of developer preview
		- {{video https://www.youtube.com/watch?v=x5PZwb4XurU}}
	- [Advancements in the Angular Router]([https://blog.angular.io/advancements-in-the-angular-router-5d69ec4c032](https://blog.angular.io/angular-v15-is-now-available-df7be7f2f4c8#ecb8)) This was available in 14.2 but I'll probably look to implement with v15.
		- Better tree-shaking in the Router removing the old `HashLocationStrategy` and SSR code if not used
			- Saves about 11% of the router code size
		- No longer need to import RouterModule directly.
			- New: `providers: [provideRouter(appRoutes)]`
			- Old: `providers: [importProvidersFrom(RouterModule.forRoot(appRoutes))]`
		- No longer need to have the `.then(m => m.Component)` boilerplate as these are unwrapped by default.
	- [Functional Router Guards] should reduce boilerplate
		- Can run guards in sequence. [See test code](https://github.com/angular/angular/blob/8546b17adec01de69bf314a959ef2d12f6638eb9/packages/router/test/integration.spec.ts#L5157-L5194)
	-
	- [Better stack traces](https://developer.chrome.com/blog/devtools-modern-web-debugging/)
	- [Further improvements to esbuild support](https://esbuild.github.io/)
		- to try change the builder to: `"builder": "@angular-devkit/build-angular:browser-esbuild"`
	- bootstrapApplication API
		- Set default date format for DatePipe
- ## Deprecations
  collapsed:: true
	- `providedIn: 'any'` is no longer valid
	- `providedIn: NgModule` no longer valid
		- > It does not have wide usage, and in most cases is used incorrectly, in circumstances where you should prefer  `providedIn: 'root'` . If you should truly scope providers to a specific  `NgModule` , use  `NgModule.providers`  instead.