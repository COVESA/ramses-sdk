# Version compatibility matrix

The following table contains the versions provided for each Ramses Composer
release along with compatibility information. In order to keep the Ramses ecosystem
manageable, we maintain strict upgrade policy - if you need a new feature of one package,
you should upgrade all the packages to the corresponding version of the toolchain.
If you have good reasons to not upgrade Ramses and/or Ramses Logic, please consult
the [library version compatibility matrix](https://ramses-logic.readthedocs.io/en/latest/readme_ref.html#version-matrix).

|Iteration|Composer |Logic    | Ramses        | Notes                                                      |
|---------|---------|---------|---------------|------------------------------------------------------------|
| 4       |0.9.2    |0.11.0   | 27.0.113      | See [dedicated upgrade section](upgrade_raco09)   |
| 3       |0.9.1    |0.10.2   | 27.0.112      | See [dedicated upgrade section](upgrade_raco09)   |
| 2       |0.8.3    |0.7.0    | 27.0.105      | Compatible to Logic 0.7.x and Ramses 27.0.100+             |
| 1       |0.8.1    |0.6.1    | 27.0.103      | Compatible to Logic 0.6.x and Ramses 27.0.100+             |

Ramses Composer is designed to remain backwards compatible to all previous versions. It will migrate project files automatically upon loading, so make sure to check in or archive your current project before trying out a new version.
You can also find information about your current version of all components in the Help->About section of the Composer.

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
        * [RenderLayers and ordering](https://github.com/COVESA/ramses-composer-docs/blob/master/ordering/manual.md)
        * [Offscreen rendering](https://github.com/COVESA/ramses-composer-docs/blob/master/offscreen/manual.md)
