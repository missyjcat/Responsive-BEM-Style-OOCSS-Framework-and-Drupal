jessCSS-BEM
===========

### Jess's OOCSS Framework using SASS and BEM

http://www.jessicachanstudios.com/

Some tenets of OOCSS followed here and some choices made:
- Layout classes are prefixed with `l-` (grid and positioning), spacing classes are prefixed with `m-` for margin and `p-` for padding.

- Objects are not prefixed (eg., `media`), but their subcomponents and modifiers are:

    - Subcomponents of objects are indicated with a `__` (double underscore):
        - `media__body`
        - `media__img`

    - Modifiers of objects are indicated with a `--` (double hyphen):
        - A `media` image subcomponent that floats to the right:
        - `media__img--right`

- Objects in the modules folder are core objects that are common to all skins. Skins can contain unique objects that are specific to that skin. One example is if you want to apply a thick top border to an element. This object could be named something like: 

```css
.bordertop--skyblue {
    border-top: 15px solid $blue;
}
```

This both creates and modifies an object. There is no base object. But it can be reused anywhere there needs to be a similar top border thick blue line.

- Try not to target elements (`h1`, `span`, etc). If you must style elements because of Drupal or some other limitation, leave a comment

- When using sizing units, instead of doing something like `margin: 5px`, use:

```css
@include rem(margin, 5px);
```

This will convert your unit of measure to `rem` (root em).

- Classes don't describe content, which enables them to be more reusable. Content classes also tempt content-specific selection. If you must label a section of the page with a content descriptor, try to use the `data-ui-component` attribute.

- IDs are reserved for elements that need to be targeted in JavaScript. Use classes only for styling.

- There are some cases where the Drupal theme will need to be altered in order to inject the appropriate classes in theme-generated markup. That's okay as long as those classes are theme-specific and are located in a skin file, or they are structure-specific, in which case they can be a base class.

- Any classes related to presentation (sizing, color, etc.) of a specific "look" should be part of a `/skin` file or a new `/skin` file.

- `!important` should **never** be used. If it is used, leave a comment.
t nest classes in SASS unless they are dependent on a parent class. This will prevent SASS from outputting redundent classes.
