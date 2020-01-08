# Applications

All applications are located in `packages/manager/apps/*` workspace.

It contains:

- Four large AngularJS monolithic applications (listed below).
- A Sign-up form.
- Several standalone applications.

An application can be started for a specific region.

| Application                   | Region       |
| ----------------------------- | ------------ |
| [Web](#web)                   | EU           |
| [Server](#server)             | EU / CA / US |
| [Public Cloud](#public-cloud) | EU / CA / US |
| [Telecom](#telecom)           | EU           |

:::tip Information
Pay attention that regarding the region, you should rely on a different API URL.
- <https://api.ovh.com/console/>
- <https://ca.api.ovh.com/console/>
- <https://api.us.ovhcloud.com/console/>
:::

## Web

![](/assets/img/control-panel-web.jpg)

### How to start the application?

```sh
$ cd packages/manager/apps/web
$ yarn run start:dev
```

### How to build the application?

```sh
$ cd - # root path of the monorepo
$ yarn run build -p @ovh-ux/manager-web
```

## Server

![](/assets/img/control-panel-server.jpg)

::: tip Information
Both applications **Dedicated** and **Cloud** are grouped under the **Server**
tab.

They can be started in different region with a given environment variable.
:::

### How to start the application?

```sh
$ cd packages/manager/apps/dedicated # or cloud
$ export REGION=CA # (Default: EU)
$ yarn run start:dev
```

### How to build the application?

```sh
$ cd - # root path of the monorepo
$ yarn run build -p @ovh-ux/manager-dedicated # or @ovh-ux/manager-cloud
```

## Public Cloud

![](/assets/img/control-panel-public-cloud.jpg)

::: tip Information
Application can be started in different region with a given environment variable.
:::

### How to start the application?

```sh
$ cd packages/manager/apps/public-cloud
$ export REGION=CA # (Default: EU)
$ yarn run start:dev
```

### How to build the application?

```sh
$ cd - # root path of the monorepo
$ yarn run build -p @ovh-ux/manager-public-cloud
```

## Telecom

![](/assets/img/control-panel-telecom.jpg)

### How to start the application?

```sh
$ cd packages/manager/apps/telecom
$ yarn run start:dev
```

### How to build the application?

```sh
$ cd - # root path of the monorepo
$ yarn run build -p @ovh-ux/manager-telecom
```
## Related

- [@ovh-ux/sao-ovh-manager-app](https://github.com/ovh/manager/blob/develop/packages/manager/tools/sao-ovh-manager-app/README.md) - Scaffolding tool for standalone applications.

## All applications

<list-packages type="applications"/>
