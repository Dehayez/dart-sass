# The use of @use #
## Why ##
> October 2021 - Start [deprecation of LibSass](https://github.com/sass/node-sass/issues/2952 "deprecation of LibSass"), including node-sass, including @import <br/>
> October 2022 - No support anymore

### Problems with @import ###
* @import makes all variables, mixins, and functions globally accessible. This makes it very difficult for people (or tools) to tell where anything is defined.
* Because everything’s global, libraries must prefix to all their members to avoid naming collisions.
* @extend rules are also global, which makes it difficult to predict which style rules will be extended.
* Each stylesheet is executed and its CSS emitted every time it’s @imported, which increases compilation time and produces bloated output.
* There was no way to define private members or placeholder selectors that were inaccessible to downstream stylesheets.

The new module system and the @use rule address all the problems above.
<br/>
<br/>

### Difference between @import and @use ###
@use does the same as @import but has some notable differences:

*  Gives variables namesspaces to prevent collision
* The file is only imported once, no matter how many times you @use it in a project.
* Variables, mixins, and functions (what Sass calls “members”) that start with an underscore (_) or hyphen (-) are considered private, and not imported.
* Members from the used fil are only made available locally, but not passed along to future imports.
* Similarly, @extends will only apply up the chain; extending selectors in imported files, but not extending files that import this one.
All imported members are namespaced by default
<br/>


<br/>
<br/>

## How ##
The [migration tool](https://sass-lang.com/documentation/cli/migrator "migration tool") automatically converts most @import-based code to @use-based code.

First of all, support for LibSass is not available yet. The extention "Live Sass Compiler" uses LibSass so RIP (for now).

### Commands ###
Install sass <br/>
`npm install -D sass`

Watch files for changes <br/>
`sass --watch scss:css`

<br/>
<br/>

## Documentation ##
[Sass Import](https://sass-lang.com/documentation/at-rules/import "sass import") <br/>
[Sass Forward](https://sass-lang.com/documentation/at-rules/forward "sass forward") <br/>
[Sass Use](https://sass-lang.com/documentation/at-rules/use "sass use") <br/>

### More ###
[Dart Sass Module System](https://css-tricks.com/introducing-sass-modules/ "Introducing Sass Modules") <br/>
