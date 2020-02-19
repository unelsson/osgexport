## Overview

A plugin for Blender 2.7 for exporting models as OSG native format (osgt). Originally created by Cedric Pinson, Jeremy Moles, Peter Amstutz and others. Original add-on discontinued, therefore from version 0.15 updates managed by Nelsson Huotari mainly for purposes of exporting models to OpenMW (https://github.com/openmw/openmw).

Version 0.15 will be the last release for Blender 2.7. Updates to Blender 2.8 are planned for version 0.16, but for the ease of upkeep, 0.16 will break compatibility with older Blender versions. Reasons are updates to Python, major changes to Blender API. Additionally, Blender dropping the support of classic shaders (Ambient, Diffuse, Specular, Emission, Opacity, Normal and Bump) requires a workaround for osgexport functionality.

Follow instruction from github to get the repository

https://github.com/unelsson/osgexport

## Installation (blender 2.7)

To install last version of the exporter go in user preference, then 'Install from File' in the Add-ons tab with the zip from https://github.com/unelsson/osgexport/releases

## Command line usage

`osgexport` needs to inject the path to exporter modules into PYTHONPATH. The injection is done by reading the value of the `BlenderExporter` environment variable (see [\_\_init\_\_.py](https://github.com/unelsson/osgexport/blob/master/exporter/osg/__init__.py#L46-51)).

```shell

$ BlenderExporter="/path-to-osgexport/blender-2.5/exporter" \
    blender -b "input.blend" \
    -P "${BlenderExporter}/osg/__init__.py" \
    -- --output="output.osgt" \
    [--apply-modifiers] [--enable-animation] [--json-materials] [--enable-animation] \
    [--bake-all] [--bake-quaternions]
```

## How to report a bug

Open an [issue](https://github.com/unelsson/osgexport/issues/new).


## Tests

To run tests:

```shell

mkdir tests && cd tests
cmake ../ -DBLENDER:FILEPATH="/my/path/to/blender" -DTEST=ON
make  # runs test building osgt files for models in blender-2.xx/data/
make test  # runs python test located in blender-2.xx/test/

```

To troubleshoot python tests:  `ctest --debug` or `ctest --output-on-failure`
