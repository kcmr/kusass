# { kusass }

**{ kusass }** is a small library of **sass mixins and functions** that I use in small projects to help me deal with BEM and unit conversion.

The unit conversion functions have been ~~stolen~~ picked from [Bourbon](http://bourbon.io).

## Installation

Install via Bower:

```bash
bower install kcmr/kusass
```

Or [download it](https://github.com/kcmr/kusass/archive/master.zip).

## Usage

Import into your main scss:

```scss
@import "kusass/kusass";
```

Override `$em-base` var if you need it. The default `font-size` is 16px.

```scss
@import "kusass/kusass";
@import "myvars";
```

In `_myvars.scss`:

```scss
$em-base: 14px;
```

## Available mixins

### BEM helpers

#### `elem`

```scss
@include elem($block, 'classname')
```

This is useful when you need to apply styles to a BEM element inside a modifier or state class.

**Example:**

```scss
.my-block {
  $block: &;
  
  &--modifier {
    @include elem($block, 'element') {
      // styles for .my-block--modifier .my-block__element
    }
  }
  
  &.is-active {
    @include elem($block, 'element') {
      // styles for .my-block.is-active .my-block__element
    }
  }
}
```

#### `mod`

```scss
@include mod($block, 'classname')
```

I'm thinking if this mixin has any utility…

## Available functions

### Unit conversion

Check out the Bourbon docs about [rem](http://bourbon.io/docs/#px-to-rem) and [em](http://bourbon.io/docs/#px-to-em) functions.

#### `rem`

Converts px to rems.

It asumes that default `font-size` is 16px. You can override the default value in your own vars file by setting the var `$em-base`.

```scss
.class { font-size: rem(12); }
// or...
.class { font-size: rem(12px); }
```

#### `em`

Converts px to ems.


```scss
.class { font-size: em(12); } 
// or...
.class { font-size: em(12px); }
// or...
.class { font-size: em(12, 18); } // uses the second value as relative unit.
```
