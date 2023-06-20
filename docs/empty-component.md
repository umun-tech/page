# Empty Component

There is a tradeoff that I had to do between `ionic-router-outlet` and `router-outlet`

`ionic-router-outlet`
- [x] provides animations and gestures
- [x] show the back button
- [x] Ionic's lifecycle hooks
- [ ] Close root page on back button

`router-outlet`
- [ ] provides animations and gestures
- [ ] show the back button
- [ ] Ionic's lifecycle hooks
- [x] Close root page on back button

Hence, I chose to use `ion-router-outlet`.


## Usage

Add `EmptyComponent` as a sibling route to your child page, if the children, doesn't redirect to a default path. This will also allow you to use the back button on the root page.
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

## Custom Empty Component

You could pass in your own empty component to the `umn-page` component. 

```ts
children: [
  {
    path: '',
    component: MyEmptyComponent
  },
  {
    path: "child",
    component: MyChildPageComponent
  }
]
```

```html
<umn-page emptyComponentClassName="MyEmptyComponent">
</umn-page>
```
