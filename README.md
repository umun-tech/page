# Umun Page

Ionic offers an effective method for mobile page navigation. However, its intuitiveness on the desktop platform is lacking. This library resolves this issue by facilitating page navigation on the desktop, while preserving the standard Ionic navigation for mobile devices.

## Inspiration

`umn-page` is inspired by how apple handles page navigation in its app while on `mobile` and `desktop`.

- On mobile, the pages are pushed on top of each other.
- On desktop, the pages are shown side by side.

## Installation

```bash
npm install @umun-tech/page
```

## Usage

### Creating a page

1. Import the `PageModule` into your feature module.
```ts
import { Page } from '@umun/page'

imports: [
  PageModule
]
```

2. Use the `umn-page` component in your template. Create an ionic page as you normally would, but wrap it in the `umn-page` component. 
```html
<umn-page>
  <ion-header>
    <ion-toolbar>
      <ion-title>Home</ion-title>
    </ion-toolbar>
  </ion-header>
  <ion-content>
    Hello World
  </ion-content>
</umn-page>
```
3. Use the [`umn-back`](./docs/umn-back.md) component in your template to add a back button to your page. This is better than the default `ionic-back-button` since it also works on window reload.

```html
<ion-header>
    <ion-toolbar>
      <ion-buttons>
        <umn-back></umn-back>
      </ion-buttons>
      <ion-title>{{title}}</ion-title>
    </ion-toolbar>
</ion-header>
```

## Navigation

### Navigating in Page Hierarchy

This is when you want to open up a page on right-side of the existing page on desktop. And on top of the existing page on mobile.

1. Import the `RouterModule` into your feature module. And create child routes for your page.
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

> This works for both mobile and desktop. On mobile, the child page will be pushed on top of the parent page. On desktop, the child page will be shown in the router outlet.

> `umn-page` will automatically handle routing on mobile, hence you don't need to provide sibling routes for mobile. 
2. [Optional] Add `EmptyComponent` as a sibling route to your child page, if the children, doesn't redirect to a default path. Read more about empty components [here](./docs/empty-component.md).
```ts
children: [
  {
    path: '',
    component: EmptyComponent
  },
  {
    path: "child",
    component: MyChildPageComponent
  }
]
```
3. Use the [`path`](./docs/path.md) directive on any ionic component, inside `umn-page` to navigate to a child page.

```html

<umn-page>
    <ion-button path="child"></ion-button>
    <ion-item path="child"></ion-item>
</umn-page>
```

> Using `path` directive will give `primary` color to the element, whenever the path (route) is active.

> Unlke routerLink, you do not need to provicde the full path. Just the child path is enough.


### Navigating outside the page

This is when you want to open up any route, but not as a child of the current page. Simply use the default `routerLink` directive.

```html
<umn-page>
    <ion-button routerLink="/home" routerLinkActive="active"></ion-button>
    <ion-item routerLink="/home" routerLinkActive="active"></ion-item>
</umn-page>
```

### Advanced Usage
- [ion-menu](./docs/advanced-usage.md#using-with-ion-menu)
- [ion-split-pane](./docs/advanced-usage.md#using-with-ion-split-pane)

### Lifecycle Hooks

All the lifecycle hooks of `ion-page` are available in `umn-page`.

- ionViewWillEnter
- ionViewDidEnter
- ionViewWillLeave
- ionViewDidLeave


## Properties

### desktopViewType

| Name | Description |
| :--- | :--- |
| Description | This allows you to show either column view, or show the page full screen on desktop. |
| Type |  `"column"` \| `"full_screen"` |
| Default | `"full_screen"` |

### contentWidthDesktop

| Name | Description |
| :--- | :--- |
| Description | This is the width the page will take, when open as `column` on desktop or tablet. |
| Type |  `number` |
| Default | 400 |

### contentWidthDesktopExpanded

| Name | Description |
| :--- | :--- |
| Description | If you are using [width-button](./docs/width-button.md) to toggle page with, `contentWidthDesktopExpanded` is the maximum size that the page will take as a column. |
| Type |  `number` |
| Default | 600 |

> Unit of both `contentWidthDesktopExpanded` and `contentWidthDesktop` is `px`.

### label

| Name | Description |
| :--- | :--- |
| Description | This is the label of the page, you may use this label to show a breadcrumb of pages. |
| Type |  `string` |
| Default | If label is not provided, it is set to the router path. |

### emptyComponentClassName

| Name | Description |
| :--- | :--- |
| Description | If you are using a custom [`empty-component`](./docs/empty-component.md) provide its class as a string here|
| Type |  `string` |
| Default | `EmptyComponent` |

## Events

| Name | Description |
| :--- | :--- |
| pathChange | Fired when a page is pushed or popped in the `ion-router-outlet` inside of `umn-page` |


## Sub Components

- [umn-back](./docs/umn-back.md)
- [width-button](./docs/width-button.md)
- [empty-component](./docs/empty-component.md)

## Directives

- [path](./docs/path.md)



## Whats New

### [0.0.3] - 16 Jun 2022

- Added default empty component.
- `pathActive` class on active paths
- Minor bug fixes

See [changelog](./docs/CHANGELOG.md) for more details.

## Contributing

Contributions are welcome. Please open up an issue or create PR if you want to contribute.

### Requested Features

- [ ] Open pages in full width of a page on desktop, just how in apple notes, notes page takes full width in the end. And there is no scroll bar.

### Open Issues

- [ ] I'm experiencing a problem where I navigate to a page that contains multiple instances of ion-menu in the ion-router-outlet. When I first navigate to the page and open the menu, it works as expected. However, when I subsequently navigate to another page layered on top, only the menu from the top page opens. The issue arises when I return to the original page: the menu fails to open as it should.
