---
layout: post
title: A compiled template engine for Golang
tags: main
---

I have asked in [go-nuts](https://groups.google.com/forum/?fromgroups=#!topic/golang-nuts/-wYJik7iL60) group that I like to have a template system that compiles to Go code. Here I will describe more about the syntax I think it should work. which I will call it `gtemplate` for now. There is nothing I have down to implement it yet but just show the idea.

## Package of gtemplate

A gtemplate package is the same as any go package, It's just a directory inside your `GOPATH`

![folder](/images/gtemplate/folder.png)

The difference for example is along side the generated go source code file `hello.go`, there is a `hello.gt` file which is using different syntax but mostly similar to Golang, but gives more convenient for writing template.

## Header part of gtemplate file

`hello.gt`:

<script src="https://gist.github.com/sunfmin/5219393.js"></script>

You can see that except the func definition, All other part of the .gt file is the same as .go source, this way you can have dependency management for template files the same as go file, and you can put struct definition that will be used for template the same place as the template definition.

## Template func

You can only define template inside a func, If you write `{ {func Hello(d *HelloData)} }`, It means the method inside is mainly for output text with fewer variable replacement and loops.

A closer look at the template func definition:

<script src="https://gist.github.com/sunfmin/5219397.js"></script>

- funcs don't have to use `{` anymore, It will look ugly if we use `{ {` to wrap a `{`
- The same with all other control statement like `if`, `for`, `switch`
- function calls are just like normal go code
- No return values can be defined in template func, It will be forced to be `err error`

What the code looks like that gtemplate generated:

<script src="https://gist.github.com/sunfmin/5219401.js"></script>

It adds an argument `w io.Writer` to any template func, and write normal template text to the writer.

Every template func automatically added the `err error` return type.

Template func could be defined on data type as well:

<script src="https://gist.github.com/sunfmin/5219531.js"></script>

So that you can put more commonly used variable as field into your data type.

[A full gtemplate file](https://github.com/sunfmin/gtemplate/blob/master/tests/templates/hello.gt) and [A full generated go source code file](https://github.com/sunfmin/gtemplate/blob/master/tests/templates/hello.go)

## What is the workflow for editing gtemplate file

I am thinking make a tool that watch all your .gt file or config your Editor to generate and compile the .go code whenever you save.

## The benefit I can think of

- Compiled template have the same compile sanity check as your go source code, Because the generated go code will be compiled by the same go compiler, So most of template errors could be caught at compile time as well, it will be impossible to write a method call or field that not exist
- Pass in as many arguments as you want to a template func call, so it's more flexible then text/template
- Compile to go source code make it run as fast as go source code, No reflect used
- Package management and distribution for templates the same as go source code, And you can use `go get` to install your template to the server
- The template is compiled along into the binary, So you don't need to copy your template over when deploy your system
- Rendering a template can be as easy as calling a go method
- Data used by template can be defined together
- No need to learn another template language, It's closest to Go syntax

You can go to [github.com/sunfmin/gtemplate](https://github.com/sunfmin/gtemplate) to check the progress on this.


