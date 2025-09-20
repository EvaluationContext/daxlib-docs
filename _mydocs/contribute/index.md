---
layout:         page
title:          Contribute to DAX Lib
menu_title:     Contribute
published:      true
date:           2025-08-14
modified:       2025-08-25
order:          /02
next_reading:   true
---

A DAX library is deployed as a package in DAX Lib. A package is a ZIP file that includes a few files (**TODO add package description**).

You can follow these steps to add a new package to DAX Lib:

1. **Clone** the GitHub repository [https://github.com/sql-bi/daxlib/](https://github.com/sql-bi/daxlib/).

2. **Create a folder** for your package in `/packages/`, for example by copying the `DaxLib.Sample` package, and follow the [naming conventions](naming-conventions.md) for package, library, and function names.

3. **Create the DAX functions** in `functions.tmdl`

    a. The file `lib/functions.tmdl` contains the source code of the DAX functions in a TMDL `createOrReplace` command. For example, in `test.functions` the name is `/packages/t/test.functions/lib/functions.tmdl`

    b. The `functions.tmdl` file contains the function definition using the TMDL syntax following the `createOrReplace` statement

    c. Include mandatory annotations for each function of the library:

       ```
       annotation DAXLIB_PackageId = <name of library>
       annotation DAXLIB_PackageVersion = <version of library>
       ```
     
4. **Create the manifest** in the `manifest.daxlib` file
    
    a. For example, in `test.functions` the name is `/packages/t/test.functions/manifest.daxlib`

    b. The `manifest.daxlib` file contains the package properties in JSON format. See the [DaxLib.Sample](https://daxlib.org/package/DaxLib.Sample/#code) package for an example and refer to the [JSON schema](https://github.com/sql-bi/daxlib/blob/main/schemas/manifest/1.0.0/manifest.1.0.0.schema.json) for the complete specification of available properties.

5. **Create a pull request** to publish the library on daxlib.org

    a. The pull request must be approved manually by DaxLib owners/maintainers.

    b. When the pull request is approved, the package is immediately published.
