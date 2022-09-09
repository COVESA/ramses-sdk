# Version compatibility matrix

The following table contains the versions provided for each Ramses Composer
release along with compatibility information. In order to keep the Ramses ecosystem
manageable, we maintain strict upgrade policy - if you need a new feature of one package,
you should upgrade all the packages to the corresponding version of the toolchain.
If you have good reasons to not upgrade Ramses and/or Ramses Logic, please consult
the [library version compatibility matrix](https://ramses-logic.readthedocs.io/en/latest/readme_ref.html#version-matrix).

|Composer |Logic    | Ramses        | Notes                                                      |
|---------|---------|---------------|------------------------------------------------------------|
|1.3.0    |1.1.0    | 27.0.121      | See [upgrade section 1.3](upgrade_raco130)                 |
|1.2.0    |1.1.0    | 27.0.121      | [Changelog](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md#120-trace-player-weak-links-and-running-python-script-in-gui-application) |
|1.1.2    |1.1.0    | 27.0.121      | See [upgrade section 1.1.2](upgrade_raco112)               |
|1.1.0-1  |x        | x             | Please skip these versions and use 1.1.2 instead           |
|1.0.x    |1.0.2    | 27.0.119      | See [upgrade section 1.0.0](upgrade_raco1)                 |
|0.14.0   |0.15     | 27.0.116      | See [notes on global symbols](upgrade_raco014)             |
|0.13.x   |0.14.2   | 27.0.115      | [Ramses Composer changelog](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md) |
|0.12.0   |0.14.2   | 27.0.115      | [Ramses Composer changelog](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md) |
|0.11.1   |0.13.0   | 27.0.114      | [Ramses Composer changelog](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md) |
|0.11.0   |0.13.0   | 27.0.114      | [Ramses Composer changelog](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md) |
|0.10.0   |0.12.0   | 27.0.113      | See [notes on animations](animations)                      |
|0.9.3    |0.12.0   | 27.0.113      | See [upgrade section 0.9.2->0.9.3](upgrade_raco093)        |
|0.9.2    |0.11.0   | 27.0.113      | See [upgrade section 0.9.x](upgrade_raco09)                |
|0.9.1    |0.10.2   | 27.0.112      | See [upgrade section 0.9.x](upgrade_raco09)                |
|0.8.3    |0.7.0    | 27.0.105      | Compatible to Logic 0.7.x and Ramses 27.0.100+             |
|0.8.1    |0.6.1    | 27.0.103      | Compatible to Logic 0.6.x and Ramses 27.0.100+             |

Ramses Composer is designed to remain backwards compatible to all previous versions. It will migrate project files upon saving with
a newer version, so make sure to check in or archive your current project before trying out a new version.
You can also find information about your current version of all components in the Help->About section of the Composer.

(upgrade_raco130)=
# Upgrade to RaCo v1.3

RaCo 1.3 exposes the possibility to use RamsesLogic feature levels. RamsesLogic supports feature
levels to allow supporting multiple versions of the content toolchain at the same time.
See more info about feature levels on the official [docs](https://ramses-logic.readthedocs.io/en/latest/api.html#file-compatibility).
See the [Changelog](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md#130-ramses-logic-feature-level-2-support-relinking-search-function-ui-improvements) for
more info how to upgrade your existing projects to use newer features of the toolchain.
The default behavior is optimized for "backwards compatibility", i.e. it will not
automatically upgrade your content.

(upgrade_raco112)=
# Upgrade from RaCo v1.0 to RaCo v1.1

Ramses Composer 1.1 (and later!) requires projects to be migrated to use interfaces instead of Lua scripts.
This improves the performance of existing scenes and also allows a more format way of interacting
with the asset using well-defined interfaces, but requires the project to be migrated first.
See the section ``Suggested migration procedure`` in the
[CHANGELOG](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md#110-lua-interfaces-various-ui-improvements)
for exact steps how to do that.

(upgrade_raco1)=
# Upgrade from RaCo v0.x to RaCo v1.0.0

Ramses Composer 1.0 (and the underlying logic engine 1.0) represent the first major version of the Ramses SDK.
To ensure extensibility for the future, it provides a new (not backwards compatible!) Lua API which allows to be
extended without breaking user code. To make the migration easy, we provide the following tools:
* Documentation of the changes
    * [Ramses Composer](https://github.com/bmwcarit/ramses-composer/blob/main/CHANGELOG.md#100-ramses-logic-1x-python-api-timer-new-animations)
    * [Ramses Logic](https://ramses-logic.readthedocs.io/en/latest/changelog_ref.html#v1-0-0)
* [Migration scripts](https://github.com/bmwcarit/ramses-logic/tree/master/tools/migrate)
* An enhanced error view in the Ramses Composer which will report errors for each API violation

The new version of the SDK also adds a lot of new functionality, please try it out and [provide feedback](https://ramses-sdk.readthedocs.io/en/latest/community.html):
* Python API for RaCoHeadless
* Reworked animations
* Timer objects
* Image conversion utilities
* ... and many more

(upgrade_raco014)=
# Global symbols in RaCo 0.14.0

The logic engine 0.15.0 disabled writing of global variables in order to make scripts safer
and less prone to undefined behavior. This includes global functions. To keep your global
symbols (if you have such), move them to the init() function and assign them to the
special GLOBAL table. Or move them to modules. For more details, read the
[docs](https://ramses-logic.readthedocs.io/en/latest/lua_syntax.html#global-variables-and-the-init-function).

(animations)=
# Animations in RaCo 0.10.0

RaCo 0.10.0 introduces a major new feature in the Ramses Ecosystem - imported animations.
This version serves as a preview and first iteration of animations to demonstrate simple
usage - start/stop, rewind etc. More advanced controls will be added in upcoming versions of
the Ramses SDK.

```{admonition} Time
:class: note

In RaCo 0.10.0 it's still not possible to control time. You have to do this over the [timeDelta
property](https://ramses-logic.readthedocs.io/en/latest/classes/AnimationNode.html#_CPPv4N6rlogic13AnimationNodeE) in Ramses Logic, e.g. by iterating over animation nodes
using the [Collections API](https://ramses-logic.readthedocs.io/en/latest/classes/LogicEngine.html#_CPPv4I0ENK6rlogic11LogicEngine13getCollectionE10CollectionI1TEv) and setting a timeDelta value in your application runtime.
This will be improved in upcoming versions of the SDK.
```

(upgrade_raco093)=
# Upgrade from RaCo v0.9.2 to RaCo v0.9.3

Ramses Logic 0.12.0 implements a more strict safety policy in terms of Lua environments which may break existing Lua scripts.
For full details, see the [the CHANGELOG of version 0.12.0](https://ramses-logic.readthedocs.io/en/latest/changelog_ref.html#v0-12-0).
Here are some hints what may be broken now:
* If you had global values set outside the interface()/run() methods, they may resolve to `nil` now
* Move these values to a new function dedicated for such storage - the [init() function](https://ramses-logic.readthedocs.io/en/v0.11.0/lua_syntax.html#global-variables-and-the-init-function)
* If you had global values set in the interface() function, those are not available anywhere outside this function any more

(upgrade_raco09)=
# Upgrade to RaCo v0.9.x

Ramses Composer v0.9 fixes multiple issues related to import of glTF content into Ramses and introduces a better way
of structuring the scene. Even though it is possible to load older projects and in most cases they will look the same,
it is possible that some things may look differently now and you have to fix them based on the new behavior.

Note: we suggest upgrading to v0.9.2 as it provides fixes and improvements which are not available in earlier v0.9.x versions.

We provide some hints for possible issues and how to solve them:

* Texture coordinates are strictly following OpenGL conventions now (see the glTF format spec for details)
    * Expected issues: some textures might be rotated upside down
    * Suggested solution: inspect the shader code and the glTF meshes to make sure UVs match texel orientation
* Rotation with multiple axes works correctly now
    * Expected issues: nodes with more than one axis of rotation might look differently
    * Suggested solution: split into multiple nodes with one rotation axis each and align in the desired order
* Content must be assigned to a RenderLayer (and RenderLayer to a render pass) in order to be rendered
    * Expected issues: newly imported content is not immediately shown
    * Suggested solution: read the documentation of the new scene setup
        * [RenderLayers and ordering](https://github.com/bmwcarit/ramses-composer-docs/blob/master/basics/ordering/README.md)
        * [Offscreen rendering](https://github.com/bmwcarit/ramses-composer-docs/blob/master/basics/offscreen/README.md)
