# Sublime ENSIME

This project provides integration with ENSIME and Sublime Text Editor 2.
It's a fork of a fork of the original sublime-ensime project, written by Ivan Porto Carrero.
This fork fixes a small bug when starting a new ensime project without a 

Sublime ENSIME strives to realize the dream of having Scala semantic services
inside a lightning fast and feature-rich text editor. Big thanks to Aemon Cannon,
Daniel Spiewak and Ivan Porto Carrero who demonstrated that this vision is possible
and inspired us to kick off the project.

## Project status

```
This fork was made by me (Shane) primarily for use by Originate, Inc's Scala training program.
```

This is a beta version. Basic things will work (for example, error highlighting),
but there might still be problems.

## Features

* Natively targets Scala 2.10.x, also supports Scala 2.9.x.

* Creates and understands `.ensime` projects (maximum one project per Sublime window,
  if you have a project with multiple subprojects only a single subproject will be available at a time).

* Integrates with SBT to generate Ensime projects from SBT projects and provides
  a command, which runs SBT compilation for the current Ensime project.

* Once your Ensime project is configured (we have a helper for that) and Ensime is run,
  Scala files in that Ensime project benefit from a number of semantic services:

    * On-the-fly typechecking and error highlighting on save. Error messages are displayed
      in the status bar when you click highlighted regions (unfortunately, Sublime Text 2 doesn't
      support programmable tooltips). Moreover, errors can be viewed in a dynamically updated buffer
      displayed with `Tools > Ensime > Commands > Show notes`.

    * Type-aware completions for identifiers (integrates into the built-in mechanism of completions
      in Sublime Text 2, depending on your configuration it might be bound to `Ctrl+Space`/`Cmd+Space` or `Tab`).

    * Type-aware go to definition (implemented by `ensime_go_to_definition` command: bind it yourself
      to your favorite hotkey or use the default `Ctrl+Click` binding on Windows/Linux or `Cmd+Click` on Mac).

* Implements experimental support for debugging. At the moment you can set breakpoints, create launch
  configurations, step through programs in the debugger, inspect program output, navigate stack traces
  and watch values of local variables. Things are far from smooth, but it might be worth a try.

## How to install?

Follow the instructions at the [scala course site](https://github.com/Originate/scala-training/blob/master/README_SUBLIME.md)

## How to use?

Open the Sublime command palette (typically bound to `Ctrl+Shift+P` on Windows/Linux and `Cmd+Shift+P` on Mac) and type `Ensime: Startup`.

If you don't have an Ensime project, the plugin will guide you through creating it.

If you already have a project, an ENSIME server process will be started in the background,
and the server will initialize a resident instance of the Scala compiler.
After the server is ready, a message will appear in the left-hand corner of the status bar.
It will read either `ENSIME` if the currently opened file belongs to the active Ensime project
or `ensime` if it doesn't. Keep an eye on this message - it's an indicator of things going well.

## Troubleshooting

If you find that some features of Ensime are not working properly (i.e. Go To Definition or Error Highlighting), then check the `Line Endings` setting in Sublime Text 2.  On Windows, the line endings is set to `Windows` by default.  Simply change this setting to `Unix` by going to `View > Line Endings` and selecting `Unix`.

## Contacts

In case if something goes wrong, let us know at dev@sublimescala.org or
submit an issue to the tracker https://github.com/sublimescala/sublime-ensime/issues/new.
Regards, the SublimeScala team.
