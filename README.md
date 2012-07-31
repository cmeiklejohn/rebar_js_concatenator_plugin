# Rebar JS Concatenator Plugin

Concatenate your JavaScript files when building your Erlang OTP
application.

## Installation

Specify ```rebar_js_concatenator_plugin``` as a dependency in your ```rebar.config```.

```erlang
{deps, [
       {rebar_js_concatenator_plugin, ".*",
        {git, "git://github.com/cmeiklejohn/rebar_js_concatenator_plugin.git", {branch, "master"}}}
]}.
```

Then, configure as a plugin in your ```rebar.config```.

```erlang
{plugins, [rebar_js_concatenator_plugin]}.
```

## Configuration

Below is an example configuration with one concatenation.  In this example, ```vendor.js``` is the destination file, compiled from both JQuery and Ember.js.  Place the below configuration in your applications ```rebar.config``` file.

```erlang
{js_concatenator, [
    {out_dir,    "priv/assets/javascripts"},
    {doc_root,   "priv/assets/javascripts"},
    {concatenations, [
        {"vendor.js", ["jquery-1.7.2.js", "ember-latest.js"], []}
    ]}
]}.
```

The following is an example which expands from the previous by uglifying
assets once concatenated.  The uglifier plugin for concatenator makes a
few assumptions: assets will end in .js, minified assets will end in
.min.js in the same output dir.

If you require more complex minification, take a look at
[rebar_js_uglifier_plugin](https://github.com/cmeiklejohn/rebar_js_uglifier_plugin).

```erlang
{js_concatenator, [
    {out_dir,    "priv/assets/javascripts"},
    {doc_root,   "priv/assets/javascripts"},
    {concatenations, [
        {"vendor.js", ["jquery-1.7.2.js", "ember-latest.js"], [uglify]}
    ]}
]}.
```
