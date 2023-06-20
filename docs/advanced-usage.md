# Advanced Usage

### Using With Ion Menu
Read more about ion menu [here](https://ionicframework.com/docs/api/menu).

```html
<umn-page [contentWidthDesktop]="800">
  <ion-menu contentId="main-content">
    <ion-header>
      <ion-toolbar>
        <ion-title>Menu Content</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">This is the menu content.</ion-content>
  </ion-menu>
  <div class="ion-page" id="main-content">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="end">
          <ion-menu-button></ion-menu-button>
        </ion-buttons>
        <ion-title>Main Content</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      This is the main content.
    </ion-content>
  </div>
</umn-page>
```

### Using With Ion Split Pane

Read more about ion split pane [here](https://ionicframework.com/docs/api/split-pane).

```html
<umn-page [contentWidthDesktop]="800">
  <ion-split-pane when="xs" contentId="main-content">
  <ion-menu contentId="main-content">
    <ion-header>
      <ion-toolbar>
        <ion-title>Menu Content</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">This is the menu content.</ion-content>
  </ion-menu>
  <div class="ion-page" id="main-content">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="end">
          <ion-menu-button></ion-menu-button>
        </ion-buttons>
        <ion-title>Main Content</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      This is the main content.
    </ion-content>
  </div>
  </ion-split-pane>
</umn-page>
```
