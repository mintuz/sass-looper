This is a small mixin to output utility classes per breakpoint.

Instead of defining CSS classes with the same properties in each class, why not create utility classes that have these properties defined once. The idea comes from http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/#utility-namespaces-u-

## Install
`bower install sass-looper --save`

## Dependencies

This library depends on Guardians sass-mq which you can read more about here http://sass-mq.github.io/sass-mq/

## Usage

### Define a scss map with your settings

##### Syntax

```
$map: ('breakpoint-name': (
  'utility-name': (
    'property-name': $property-value
  )
),
'breakpoint-name': (
  'utility-name': (
    'property-name': $property-value
  )
));
```

##### Example

```
$map: ('small': (
  'margin-bottom': (
    'margin-bottom': 8px
  )
),
'medium': (
  'margin-bottom': (
    'margin-bottom': 16px
  )
));
```

You might be thinking, why are you specifying margin-bottom twice for each breakpoint. Well the idea is that you can name your utilites whatever you want. I like having my classes named `.u-margin-bottom` but you can name them whatever you like.

For example

```
$map:('small': (
  'taylor-swift': (
    'margin-bottom': 8px
  )
),
'medium': (
  'taylor-swift': (
    'margin-bottom': 16px
  )
));
```

Would output

```
.u-taylor-swift {
  margin-bottom: 8px;
}
```

### Calling the library

```
$mq-breakpoints: (
  small:  320px,
  medium:  740px
);

$map:('small': (
  'taylor-swift': (
    'margin-bottom': 8px
  )
),
'medium': (
  'taylor-swift': (
    'margin-bottom': 16px
  )
));

@import 'bower_components/sass-mq/mq';
@import 'bower_components/sass-looper/sass-looper';

@include sass-looper('my-namespace-', $map);
```

