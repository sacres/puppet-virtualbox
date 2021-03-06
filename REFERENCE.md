# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Classes**

_Public Classes_

* [`virtualbox`](#virtualbox): Installs VirtualBox.

_Private Classes_

* `virtualbox::install`: installs the VirtualBox package
* `virtualbox::kernel`: compiles and installs the VirtualBox kernel modules
* `virtualbox::params`: It sets variables according to platform

**Defined types**

* [`virtualbox::extpack`](#virtualboxextpack): This class (un)installs Oracle's VirtualBox extension pack.

## Classes

### virtualbox

Installs VirtualBox.

#### Parameters

The following parameters are available in the `virtualbox` class.

##### `version`

Data type: `String`

The major version of the package to install.

Default value: '5.1'

##### `package_ensure`

Data type: `String`

This gets passed to the package resource as the value of the 'ensure'
parameter. This can be used to specify a package version.

Default value: 'present'

##### `manage_repo`

Data type: `Boolean`

Should this module manage the package repository?
Defaults to true

Default value: $virtualbox::params::manage_repo

##### `manage_ext_repo`

Data type: `Boolean`

On applicable platforms, should this module manage the external dependency
repository when `manage_kernel` is set to true?
Defaults to true

Default value: `true`

##### `repo_proxy`

Data type: `Optional[String]`

proxy used by yum

Default value: `undef`

##### `manage_package`

Data type: `Boolean`

Should this module manage the package?
Defaults to true

Default value: `true`

##### `manage_kernel`

Data type: `Boolean`

Should this module install the VirtualBox kernel modules?
Defaults to true

Default value: `true`

##### `vboxdrv_dependencies`

Data type: `Array`

Dependencies for building the VirtualBox kernel modules.
Defaults depend on the platform. See virtualbox::params.

Default value: $virtualbox::params::vboxdrv_dependencies

##### `package_name`

Data type: `String`

The name of the package to install. This must be the full packge name when
not the default. When the default is in use, it gets compounded with the
major.minor components of the version number.
Defaults to 'VirtualBox' for RedHat and 'virtualbox' for Debian

Default value: $virtualbox::params::package_name

## Defined types

### virtualbox::extpack

This class (un)installs Oracle's VirtualBox extension pack.

#### Parameters

The following parameters are available in the `virtualbox::extpack` defined type.

##### `source`

Data type: `String`

Download extension pack from the given URL. Required string.

##### `ensure`

Data type: `Enum['present', 'absent']`

Set to 'present' to install extension pack. Set to 'absent' to uninstall.
Defaults to 'present'

Default value: 'present'

##### `verify_checksum`

Data type: `Boolean`

Whether to verify the checksum of the downloaded file. Optional boolean.
Defaults to true.

Default value: `true`

##### `checksum_string`

Data type: `Optional[String]`

If $verify_checksum is true, this is the checksum to use to validate the
downloaded file against.

Default value: `undef`

##### `checksum_type`

Data type: `Enum['md5', 'sha1', 'sha224', 'sha256', 'sha384', 'sha512']`

If $verify_checksum is true, this is the algorithm to use to validate the
checksum. Can be md5, sha1, sha224, sha256, sha384, or sha512. Defaults to
'md5'

Default value: 'md5'

##### `follow_redirects`

Data type: `Boolean`

If we should follow HTTP redirects. Ignored when using `puppet/archive`.
Defaults to false.

Default value: `false`

##### `extpack_path`

Data type: `Stdlib::Absolutepath`

This is the path where VirtualBox looks for extension packs. Defaults to
'/usr/lib/virtualbox/ExtensionPacks'

Default value: '/usr/lib/virtualbox/ExtensionPacks'

##### `archive_provider`

Data type: `Optional[Enum['puppet','puppet-community','voxpupuli','camptocamp']]`

This param eter is used to tell the module which `archive` module to expect.
This can be set to the Puppet Forge username of the developer of the
`archive` module you wish to use. If a falsey value is passed, this module
will try and determine the module author by using the `load_module_metadata`
function from Stdlib. This is the default behavior. Defaults to `undef`.

Default value: `undef`

