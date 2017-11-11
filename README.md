# AngularTranslation

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.5.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
Create and installing 
====================================
ng new multilingual --prefix fss
npm install @ngx-translate/core --save
npm install @ngx-translate/http-loader

Json
========================================
-create folder i18n into assets
-put translation files 


app.module
=========================================

##import { HttpClient, HttpClientModule } from '@angular/common/http';
##import { TranslateLoader, TranslateModule } from '@ngx-translate/core';
##import { TranslateHttpLoader } from '@ngx-translate/http-loader';


export function HttpLoaderFactory( http: HttpClient) {
  return new TranslateHttpLoader(http);
}

        HttpClientModule,
        TranslateModule.forRoot({
          loader:{
            provide: TranslateLoader,
            useFactory: HttpLoaderFactory,
            deps: [HttpClient]
          }
        })

app.component
============================================

##import { TranslateService } from '@ngx-translate/core';

 user = {
    name: 'Juan Perz',
    age: 20};

constructor(private translate: TranslateService) {
    translate.setDefaultLang('en');
  }

  switchLanguage(language: string) {
    this.translate.use(language);
  }

app.component.html
==============================================

<h1 translate>{{'Title' | translate:title}}</h1>

<div>
  {{ 'Intro' | translate:user }}
  {{'City' | translate:city}}
</div>
<button (click)="switchLanguage('en')">en</button>

<button (click)="switchLanguage('fr')">fr</button>
<button (click)="switchLanguage('br')">br</button>
