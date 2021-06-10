You have an existing application or toolchain and wonder if and how you can adopt Ramses? In the sections below you can find multiple options how to do that.

# Export data from DCC tools

The way for Ramses to integrate with Digital Content Creation tools (DCC for short) is over the [glTF](https://github.com/KhronosGroup/glTF) format.
The reason we chose glTF over other industry standards (COLLADA, FBX, among others) is that it is closely aligned with OpenGL and as such leaves little
room for interpretation (which has been traditionally a major problem for many existing 3D toolchains). We have been pleased to see a widespread adoption
of glTF in existing tools, which reinforces our commitment to the format.

The reason why we support **only** glTF and no other format is the same as the reason to choose glTF in the first place. We want to keep Ramses small, well
specified, data-centric and cross platform, and we don't want to depend on proprietary or closed formats. We belive glTF is superior compared to other formats in
this aspect. If you need a different format, we suggest using the excellent Blender import/export functionality to import your format of choice and export
glTF, or write your own converter by using one of the many glTF support libs available for almost every language out there.

Currently, we support importing glTF data over the [Ramses Composer](./projects.md#the-ramses-composer) which supports both manual import over
the GUI as well as automated conversion using the headless version.
We may consider adding a runtime utility in the future,
especially if the [community](./community.md#contact) needs such.

# Composit existing OpenGL apps with Ramses

Ramses supports a feature called `embedded compositing` to integrate existing OpenGL applications with minimal performance overhead.
It allows having another application which supports the Wayland protocol to send its rendered surface to a Ramses renderer and
blend it with the rest of the Ramses scene. For details, please check the [Ramses docs](https://genivi.github.io/ramses/).

# Embed a new Ramses application in your existing framework

Using the same mechanism as above, it is possible to integrate a Ramses renderer into an existing application using the Wayland protocol.
Ramses supports two ways to do that - using the `wl_shell` protocol and using the `ivi_application` protocol.
For details, please check the [Ramses docs](https://genivi.github.io/ramses/).

# Which method is for me?

You really want to use Ramses, but aren't sure which strategy would cost the least effort or bear the least risk?
[Contact us](./community.md#contact) and we can provide guidance!
