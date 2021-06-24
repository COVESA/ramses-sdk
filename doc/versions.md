# Version compatibility matrix

The following table contains the exact versions provided for each Ramses Composer
release along with compatibility information. In order to keep the Ramses ecosystem
manageable, we maintain strict upgrade policy - if you need a new feature of one package,
you have to upgrade all the packages to the corresponding version of the toolchain.

|Composer |Logic    | Ramses        | Notes                                             |
|---------|---------|---------------|---------------------------------------------------|
|0.8.1    |0.6.1    | 27.0.103      | Compatible to Logic 0.6.x and Ramses 27.0.100+    |
Ramses Composer is designed to remain backwards compatible to all previous versions. It will migrate project files automatically upon loading, so make sure to check in or archive your current project before trying out a new version.
You can also find information about your current version of all components in the Help->About section of the Composer.
