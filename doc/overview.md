# What is Ramses?

Ramses is a low-level rendering engine which is optimized for embedded hardware -
mobile devices, automotive ECUs, IoT electronics. It is closely aligned
to Khronos APIs (OpenGL, glTF, EGL) and other industry standards (Wayland,
Freetype, etc.). Ramses has one distinguishing feature - it allows rendering
content remotely, similar to video streaming, but for 3D graphics, in an efficient
yet powerful way.

# Who created Ramses and why?

Ramses was initially developed at the BMW Group and open-sourced in 2018 as part of
a collaboration initiative with the Genivi Alliance. Despite being an important
part of the BMW infotainment cluster and digital portfolio, we decided that
we want to collaborate with other OEMs and suppliers on the fundamentals, and
specialize on the applications and customization. We feel like open sourcing Ramses was the best
way to support this strategy, and doing so has created new opportunity for us. We took inspiration from
other peers in the open source industry - the Linux kernel, the Unreal Engine,
Android, Blender, MESA and many others. We want to join the effort to make software
better, more transparent and reliable to the end user, and we firmly believe open
source development and standards are the way to achieve this goal.

Some of the Ramses components and initiatives are developed together with other partners:

* The Ramses Composer, developed by [Paradox Cat](http://paradoxcat.com/)
* The Ramses Citymodel Demo, developed by MentorGraphics, now part of [Siemens](https://eda.sw.siemens.com)
* Studies on distributed HMI technologies, together with the [Genivi alliance](https://www.genivi.org/)

# What if BMW decides to stop supporting Ramses?

All of the tools, libraries
and frameworks you will find as part of this SDK are used and deployed in BMW cars.
This requires a certain commitment from BMW to support, develop and drive Ramses today and in the future.
Furthermore, the licenses we choose (primarily MPL 2.0) allow for
flexible usage and improvement of the Ramses ecosystem - even if BMW decides to step
back from it in the future.

# When to use and when not to use

It's very difficult to answer this question absent context of application needs and requirements,
so take our reasoning below with a grain of salt!

If **one or more** of the following is true, Ramses may be a good fit for you:

* You produce/maintain 3D software for embedded devices with performance and/or memory limits
* You want to use a free and open source library for rendering
* You want to composite different sources of 3D and/or 2D data into one scene (3D compositing)
* You need a cross-platform solution which promises the same results across OS and drivers
* You don't want to write "yet another OpenGL wrapper", but you want to stay close to native performance and adopt modern OpenGL features
* A game engine is overkill for you (e.g. Unity, Godot, Unreal engine)
* You need to offer interactive content over network, and video streaming is not an option
* You want the option to have custom shaders instead of relying on a specific lighting/shading model

If some of the below are true for you, there could be a better alternative than Ramses:

* You mostly have 2D UI/UX (consider using a UI framework like Qt, wxWidgets, Flutter)
* Network bandwidth is not a problem and video streaming would work fine (consider using gStreamer or similar)
* Your application is not native (e.g. JavaScript web app) - consider using a WebGL framework (e.g. ThreeJS or BabylonJS)
* Hardware limits are not a problem for you - consider using a full-fledged Game engine (Godot, Unreal Engine etc.)


