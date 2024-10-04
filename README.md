__Forked from https://gitlab.com/dmp-repo/js-pkg/ngx-d3__

`ngx-d3` is a [D3](https://github.com/d3/d3) wrapper service for [Angular](https://angular.io/) applications inspired by [@tomwanzek/d3-ng2-service](https://github.com/tomwanzek/d3-ng2-service).

Sadly, tomwanzek is no longer maintaining the project. The last push for his library was in April 2018 and the latest supported version of angular is Angular 5. The torch of keeping the package up to speed in terms of angular compatibility was then passed onto ZeevKats's [@katze/ngx-d3](https://www.npmjs.com/package/@katze/ngx-d3) package, which kept the package updated up to angular 12, and finally to dmp's [@d-m-p/ngx-d3](https://www.npmjs.com/package/@d-m-p/ngx-d3) which kept it updated up to angular 16.

The package appears to be no longer maintained as it has now fallen behind a couple versions and I am taking over the mantle.

---
### Installation

```
yarn add ngx-d3-wrapper
```
---
### Usage

* `NgxD3Service`: The Angular D3 Service injectable,
* `D3`: A TypeScript type alias for the `d3` variable which can be obtained from the `NgxD3Service`, and
* the various TypeScript interfaces and type aliases which are related to the D3 modules constituting `d3` as provided by this service (e.g. `Selection`, `Transition`, `Axis`).

To obtain the `d3` object from an injected D3 service `ngxD3Service: NgxD3Service`, it offers a method `ngxD3Service.getD3()` with return type `D3`.

---
### How to use

```ts
import { Component, OnInit } from '@angular/core';
import { NgxD3Service } from 'ngx-d3-wrapper';

@Component({
  selector: 'histogram-component',
  templateUrl: 'histogram-component.component.html',
  styleUrls: ['histogram-component.component.css']
})
export class HistogramComponent implements OnInit {
  private readonly d3 = this.ngxD3Service.getD3();

  constructor(private readonly ngxD3Service: NgxD3Service) {}

  ngOnInit() {
    this.d3.select(...)
    // ...
  }
}
```


### Publishing
```shell
> rm -rf dist/ node_modules/ libs/ngx-d3/node_modules/
> npm run build -- -c production
> cd dist/libs/ngx-d3
> npm publish --access public
```
