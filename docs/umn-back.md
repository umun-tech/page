# umn-back

Since the `ion-back-button` does not show on page reload, I have created `umn-back` to help users navigate back, even if the page is reloaded.

> IMPORTANT: Only use the `umn-back` inside of a `umn-page` component, since the page component automatically configures the back button.

## Properties

### label
| Name | Description |
| :--- | :--- |
| Description| This is the label on the back button |
| Type | `string` |
| Default | "Back" |

### icon
| Name | Description |
| :--- | :--- |
| Description| This is the icon on the back button |
| Type | `string` |
| Default | "chevron-back" |

### showOnPageReload
| Name | Description |
| :--- | :--- |
| Description| If or not to show the back button on page reload. |
| Type | `boolean` |
| Default | `true` |


> To behave exactly as ionic either use `ion-back-button` or set `showOnPageReload` to `false`.
