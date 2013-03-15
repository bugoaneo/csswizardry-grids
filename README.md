# csswizardry-grids

**Simple, fluid, nestable, flexible, Sass-based, responsive grid system.**

* Fully responsive
* Mobile first
* Infinitely nestable
* Reversible/reorderable
* With/without gutters
* Endless possible combinations
* Simple to understand, human-friendly classes
* Option to keep classes out of your HTML
* Robust
* Simple
* No `.clear` or `.last` classes
* It just _works_

Please see [Responsive grid systems; a solution?](http://csswizardry.com/2013/02/responsive-grid-systems-a-solution/)
for a comprehensive overview of the principles of the grid system.

## Demo

* [csswizardry.github.com/csswizardry-grids](http://csswizardry.github.com/csswizardry-grids).
* [Writeup](http://csswizardry.com/2013/02/introducing-csswizardry-grids/)

## Setup

Simply fill in/adjust the relevant variables.

* `$responsive` is used to turn csswizardry-grids’ responsive features on and
  off. csswizardry-grids is designed primarily for responsive builds but can
  also be used on non-responsive projects just as easily. Setting this to false
  will simply prevent Sass generating your `palm` etc modifiers.
* `$gutter` controls how much space there is between columns.
* `$mobile-first` controls whether you would like unclassed grid items to
  _initially_ adopt `width:100%;. This means that you won’t need to add a class
  to force a grid item to take up the full width of its container.
* `$use-silent-classes` tells csswizardry-grids whether to go ahead and compile
  solid, traditional classes (e.g. `.one-whole`) or to create Sass ‘silent’
  classes which only compile to CSS once explictly called.
* `$lap-start` and `$desk-start` tell csswizardry-grids when to fire particular
  media queries to service those particular sizes. Note that csswizardry-grids
  works out the ends of any other breakpoints by using these numbers.

## Usage

csswizardry-grids is incredibly simple to implement, its classes are all
human-readable and follow the same pattern.

### Classes in markup

If you are using traditional classes then an example, basic usage might look
like this:

    <div class="grid">
    
        <div class="grid__item  lap-one-half  desk-two-thirds">
            ...
        </div><!--
    
     --><div class="grid__item  lap-one-half  desk-one-third">
            ...
        </div>
    
    </div>

It’s as simple as that!

**Note the empty HTML comments.** These are to remove whitespace caused by using
`inline-block`.  Prior to v1.1 this was tackled by using some
[`[letter|word]-spacing` trickery](https://github.com/csswizardry/csswizardry-grids/blob/60a5075ac65282bb24fa5a5d5ed32a060ce2975f/csswizardry-grids.scss#L64-L65),
however Chrome 25 introduced a change which meant this method now broke
csswizardry-grids.

### Sass’ silent classes

If you are using silent classes (`$use-silent-classes: true;`) then your HTML
might look like this:

    <div class="page">
    
        <div class="content">
            ...
        </div><!--
    
     --><div class="sub-content">
            ...
        </div>
    
    </div>

…and your Sass, something like this:

    .page{
        @extend %grid;
    }
    
        .content,
        .sub-content{
            @extend %grid__item;
            @extend %one-whole;
            @extend %lap-one-half;
        }
    
        .content{
            @extend %desk-two-thirds;
        }
    
        .sub-content{
            @extend %desk-one-third;
        }

### Reversed grids

csswizardry-grids has the option to reverse a set of grids; this means that the
order you write your source and the order it renders are total opposites, for
example:

    <div class="grid--rev">

        <div class="main-content  grid__item  two-thirds">
            I appear first in the markup, but render second in the page.
        </div><!--

     --><div class="sub-content  grid__item  one-third">
            I appear second in the markup, but render first in the page.
        </div>

    </div>

This is handy if you want to lay out your page a certain way visually but it
would be advantageous to order the source differently, for example to aid
accessibility (getting a screenreader to read more important content first).

### Gutterless grids

It may be desirable at times to have no gutter between your grid items; with
csswizardry-grids this is as simple as:

    <div class="grid--full">

        <div class="grid__item  one-half">
            Look, ma! No gutter!
        </div><!--

     --><div class="grid__item  one-half">
            Look, ma! No gutter!
        </div>

    </div>

## Help and questions

If you have any trouble setting csswizardry-grids up, or would like some help
using and implementing it (or any questions about how it works) then please feel
free to [fire me a tweet](https://twitter.com/csswizardry) or
[open an issue](https://github.com/csswizardry/csswizardry-grids/issues/new).

csswizardry-grids’ Sass can look a little daunting, but it’s doing quite a lot
of work behind the scenes to make it as simple as possible when it comes to
implementation.
