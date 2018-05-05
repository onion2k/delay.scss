# delay.scss

A library of SCSS functions for calculating animation-delay values.

# Usage

Copy the function you need in your SCSS code, or use `include delay.scss` to load them all, then use `#{<function>(<rows>, <number>)}` to calculate the timing offset for that child element. `<rows>` is the number of rows in the grid. `<number>` is the nth-child() value (eg 1 for the first, 2 for the second, and so on.)

## Example

A 6x6 grid of 36 elements would look like this;

```
@for $i from 1 through 36 {
  div:nth-child(#{$i}) { animation-delay: calc(#{linear(6, $i)} * 100ms); }
}
```

As delay.scss is a preprocessor utility there isn't a nice way to use it with an unknown number of grid elements. However, if you have to, you could just use a loop with a large number of items.

## More control using CSS vars

If you're not targeting older browsers it's nice to use a CSS var to get more control over the timing of the animation.

```
:root {
  --delay: 100ms;
}

@for $i from 1 through 36 {
  div:nth-child(#{$i}) {
    animation-delay: calc(#{linear(6, $i)} * var(--delay));
  }
}
```

This affords you the opportunity to change the timing value in the browser using devtools or JavaScript.

# Examples

Collection: https://codepen.io/collection/DdvVGP/

* Row: https://codepen.io/onion2k/pen/NMbdpM
* Column: https://codepen.io/onion2k/pen/MGbJox
* Diagonal: https://codepen.io/onion2k/pen/MGbJXd
* Chevron: https://codepen.io/onion2k/pen/jxmPmE
* Snake: https://codepen.io/onion2k/pen/MGyPvZ
* Spiral: https://codepen.io/onion2k/pen/wjdxdG
* Droplet: https://codepen.io/onion2k/pen/XqgqBw
* Clock: Coming soon (maybe)
