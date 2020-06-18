---
edit_link: ''
title: Debug the Application
origin_url: >-
  https://raw.githubusercontent.com/automotive-grade-linux/docs-sources/flounder/docs/getting-started/app-workflow-debug-app.md
---

<!-- WARNING: This file is generated by fetch_docs.js using /home/boron/Documents/AGL/docs-webtemplate/site/_data/tocs/getting_started/flounder/flounder-image-development-workflow-getting-started-book.yml -->

# Debug the Application #

You can debug your application many ways.
The method depends on factors such as the component you are debugging,
whether or not you are doing a post-mortem analysis, and your debugging
skills and productivity.
For example, do you know how to use the
[GNU Project Debugger](https://www.gnu.org/software/gdb/) (`gdb`) from a
console?
Or, is it better for you to use a remote user interface that is part of
an Integrated Development Environment (IDE) such as Eclipse?

For general information on debugging an application, see the
"[Overview](../../../devguides/reference/xds/part-1/debug-overview.html)"
topic under "Debugging Your First AGL Application".

Three methods exist:

   * Use `gdb` on the target.

     <!--section-note-->
     **NOTE:**

     How to use `gdb` and other debugging tools such as `valgrind`, `strace`,
     and so forth is beyond the scope of the AGL Documentation.
     See the appropriate documentation for third-party debugging tools.
     <!--end-section-note-->

   * Use Core Dumps if you have set the `agl-devel` feature.
     Core Dumps are obviously more suited for post-mortem analysis.
     For features, see the
     "[Initializing Your Build Environment](./image-workflow-initialize-build-environment.html#initializing-your-build-environment)"
     topic.

     <!--section-note-->
     **NOTE:**

     Core Dumps are available only with the "Flunky Flounder" release (i.e. 6.x).
     <!--end-section-note-->

   * Use XDS remotely, which is based on `gdb` and
     [`gdbserver`](https://en.wikipedia.org/wiki/Gdbserver).
     See the
     "[Using the XDS Command Line](../../../devguides/reference/xds/part-1/debug-cmd-line.html#xds-remote-debugging-mode)"
     topic for more information.

     For information on how to remotely debug the application using XDS from within an IDE, see the
     "[Using an IDE](../../../devguides/reference/xds/part-1/debug-ide.html)"
     section.

   In order to use third-party debugging tools, you need to include the tools in the target image.
   You gain access to the tools by enabling the `agl-devel` feature when you run the
   `aglsetup.sh` script as described in the
   "[Initializing Your Build Environment](./image-workflow-initialize-build-environment.html#initializing-your-build-environment)"
   section.