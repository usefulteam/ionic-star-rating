# Ionic Star Rating

This library was a copy of https://github.com/JeongJun-Lee/ionic5-star-rating which was forked from https://github.com/melwinVincent/ionic4-star-rating . Thanks for them and their community.

This library is intended to work with the latest version of Ionic.

# Ionic Star Rating

You can give your custom icons, custom color, custom font-size and also make it read-only.  

You can specify the total number of icons to be displayed, default is set to 5. You may change this to 10 star rating component or 7 star rating component depending on your requirement.  

**Supports Half Star Rating.**    
Single tap on default-star-icon changes it to half-star-icon, tap on half-star-icon changes it to full-star-icon and tap on full-star-icon changes it to half-star-icon. The rating value then steps by 0.5 instead of 1.  

You can use it multiple times in a single page/multiple pages and get the changed rating value in the parent component.  

You can also use it inside the `<form>` component (multiple use inside `<form>` is also supported).

## How to use

### Install it
`npm install https://github.com/usefulteam/ionic-star-rating/tarball/master`

### add the ionic-star-rating component in your page.html (parent component) as follows

```
<ionic-star-rating #rating
  activeIcon = "ios-star"
  defaultIcon = "ios-star-outline"
  activeColor = "#488aff" 
  defaultColor = "#f4f4f4"
  readonly="false"
  rating="3"
  fontSize = "32px"
</ionic-star-rating>
```

### to use inside the `<form>` component

```
<form [formGroup]="customForm">

  <ionic-star-rating #rating 
    activeIcon = "ios-star"
    defaultIcon = "ios-star-outline"
    activeColor = "#d1301a"
    defaultColor = "#aaaaaa"
    readonly = "false"
    fontSize = "32px"
    formControlName="starRating">
  </ionic-star-rating>

</form>
```
## Options (all are optional, default values are set in the component itself)

* activeIcon (string) : can specify the icon name for active rating (icon name should be from the https://ionicframework.com/docs/ionicons/  ,  default is set to 'ios-star');
* defaultIcon (string): can specify the default icon name (icon name should be from the https://ionicframework.com/docs/ionicons/  , default is set to 'ios-star-outline');
* halfIcon (string) : can specify the icon name for active half rating (icon name should be from the https://ionicframework.com/docs/ionicons/  ,  default is set to 'ios-star-half');
* halfStar (string) : to support half star rating set this to 'true', default is set to 'false'. The rating value then steps by 0.5 instead of 1. Single tap on defaultIcon changes it to halfIcon , tap on halfIcon changes it to activeIcon and tap on activeIcon changes it to halfIcon again.
* maxRating (number) : can specify the total number of icons to be displayed, default is set to 5. You may change this to 10 star rating component or 7 star rating component depending on your requirement.
* activeColor (string): can specify the active color for the active rating icon (should be a valid color code, default is set to '#488aff')
* defaultColor (string): can specify the default color for the rating icon (should be a valid color code, default is set to '#f4f4f4')
* readonly (string): default is set to "false", change to "true" and make it read only. End user won't be able to change the rating then.
* rating (string or number): default is set to 3. input can be of type **number** or **string** (*assign any number from 1 to 5, floating numbers are also accepted, Math.round(parseFloat(rating) is done for all inputs*). 
* fontSize (string) : can specify the font-size for the icon ( should be a valid string as used in css, a number followed by letters 'px', default is set to '28px'). 
* ratingChanged (funtion) : used to handle the rating change in the parent component and do your stuff
* formControlName : only if you are using the ionic-star-rating component inside the `<form>` component  

## Multiple usage of the component in same parent page

### parent-component.html

```
  <ionic-star-rating #rating
    activeIcon = "ios-star"
    defaultIcon = "ios-star-outline"
    activeColor = "#ff0000"
    defaultColor = "#aaaaaa"
    readonly = "false"
    rating = "2"
    fontSize = "32px"
  </ionic-star-rating>

  <ionic-star-rating #rating2
    activeIcon = "ios-star"
    defaultIcon = "ios-star-outline"
    activeColor = "#d1301a"
    defaultColor = "#aaaaaa"
    readonly = "false"
    rating = "3"
    fontSize = "32px"
  </ionic-star-rating>

```

## Multiple usage of ionic-star-rating component in the same `<form>` of the parent page

### parent-component.html
```
<form [formGroup]="customForm">

  <ionic-star-rating #rating 
    activeColor = "#ff0000"
    defaultColor = "#aaaaaa"
    readonly = "false"
    formControlName="starRating">
  </ionic-star-rating>

  <ionic-star-rating #rating2 
    activeColor = "#ff0000"
    defaultColor = "#aaaaaa"
    readonly = "false"
    formControlName="starRating2">
  </ionic-star-rating>

</form>
```

### parent-component.ts

```

import { Component } from '@angular/core';
import { FormBuilder, FormGroup } from '@angular/forms';

@Component({
  selector: 'app-tab1',
  templateUrl: 'tab1.page.html',
  styleUrls: ['tab1.page.scss']
})

export class Tab1Page {

  customForm: FormGroup;
  
  constructor( private formBuilder: FormBuilder ) {
    // do your stuff
  }
  
  ngOnInit() {

    this.customForm = this.formBuilder.group({
      // set default initial value
      starRating: [3], 
      starRating2: [4]
    });

  }

}
```

## Thanks

- https://github.com/JeongJun-Lee/ionic5-star-rating
- https://github.com/melwinVincent/ionic4-star-rating
- The communities