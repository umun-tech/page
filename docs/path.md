# path

Path directive can be used instead of `routerLink` inside a `umn-page`. It opens a page inside of the umn-page.

The page is opened in a right column if the user is accessing the page from a `desktop` of `tablet` screen-size. Otherwise the page is opened on top of the existing page on `mobile`.

## Properties

### path

| Name | Description |
| :--- | :--- |
| Description| Path to be opened as a child, do not pass the whole path from the route, only provide child path. |
| Type | `string` |
| Default | "" |


So, if you have `MyChildPageComponent` as a child of your page, and have given the path as `child`. You may simply open up this child page using `path="child"` on any component inside of your page.

```ts
 imports: [
    PageModule,
    RouterModule.forChild([
      {
        path: "",
        component: MyPageComponent,
        children: [
          {
            path: "child",
            component: MyChildPageComponent
          }
        ]
      }
    ])
  ]
```


```html
<umn-page>
    <ion-button path="child"></ion-button>
    <ion-item path="child"></ion-item>
</umn-page>
```

> You may put the directive on any component, be it ionic or otherwise.


### params

| Name | Description |
| :--- | :--- |
| Description| These are the  query parameters to be passed to the sub-page. |
| Type | import { Params } from "@angular/router"; |
| Default | "[]" |


### paramsHandling

| Name | Description |
| :--- | :--- |
| Description| This is exactly like `QueryParamsHandling` in angular. |
| Type | 'merge' | 'preserve' | '' |
| Default | "merge" |

### activeColor

| Name | Description |
| :--- | :--- |
| Description| Changes `style.color` of an element, when the path is active. |
| Type | 'string' |
| Default | "var(--ion-color-primary)" |

> Apart from changing the `font-color`, path directive also adds a class `pathActive` to the component, when the path is active. You may use this class add custom css.

### color

| Name | Description |
| :--- | :--- |
| Description| Changes `style.color` of an element, when the path is not-active. |
| Type | 'string' |
| Default | "" |


