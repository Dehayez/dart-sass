oktober 2021 - start deprecation node-sass
oktober 2022 - geen support

import doet hetzelfde als use, maar het geeft de variablen namespaces om collision te voorkomen


Verschillen tussen [Import](https://sass-lang.com/documentation/at-rules/import "Named link title") en forward/use
The file is only imported once, no matter how many times you @use it in a project.
Variables, mixins, and functions (what Sass calls “members”) that start with an underscore (_) or hyphen (-) are considered private, and not imported.
Members from the used file (buttons.scss in this case) are only made available locally, but not passed along to future imports.
Similarly, @extends will only apply up the chain; extending selectors in imported files, but not extending files that import this one.
All imported members are namespaced by default

Commands
	install sass
	npm install -D sass

	watch files for changes
	sass --watch scss:css