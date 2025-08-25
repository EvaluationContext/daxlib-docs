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

2. **Create a folder** for your package in `/packages/`, for example by copying the `DaxLib.Sample` package.

    a. Name the folder after your package using lowercase names (e.g., `test.functions`), while the package should have a pascal naming convention (e.g., `Test.Functions`).

    b. The package and library name is the prefix of all the function names. For example, to functions `Sum` and `Multiply` in the `Test.Functions` library package should be named `Test.Functions.Sum` and `Test.Functions.Multiply`.

    c. The package and library name must have a hierarchical nomenclature, where the first name is the published/author identifier and the second (and following) names identify the library scope. For example, `Contoso.Conversion` is a library of conversion functions made by Contoso, whereas `Northwind.Math.Geometry` is a set of geometrical mathematical functions made by Northwind.

    d. Do not use `Dax.` in the name of the library (Dax as a single word is a reserved keyword in a function name).

    e. `DaxLib.` as a prefix is a reserved word for public open-source libraries of common use that are reviewed and approved by DaxLib maintainers. Do not create pull request for new `DaxLib.` libraries. 

    f. The first level in the folder structure is a single letter corresponding to the first letter of the package name (for example, a package `test.functions` will be in `/packages/t/test.functions/` folder). This is a technique used to reduce the number of elements in a single folder.

    g. All the names of folders and files must be lowercase; the name of the package (with uppercase letters if necessary) is defined in the metadata (`manifest.daxlib` file) of the package.

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
