---
layout:         page
title:          Naming conventions
published:      true
date:           2025-09-20
modified:       2025-09-20
order:          /002
next_reading:   true
---

When creating a new package for DAX Lib, it is important to follow specific naming conventions to ensure consistency and clarity across the platform. Below are the key guidelines to adhere to when naming your package and its components:
1. **Package Folder Name**: The folder name for your package should be in lowercase letters and use dots to separate different levels of hierarchy. For example, if your package is named `Test.Functions`, the folder should be named `test.functions`.
2. **Package and Library Name**: The name of the package and library should follow PascalCase naming conventions, where each word starts with an uppercase letter and there are no spaces or underscores. For example, `Test.Functions` is a valid package name. Exceptions are allowed for well-known acronyms (e.g., `XML`, `JSON`, `SVG`) which can be in uppercase.
3. **Hierarchical Nomenclature**: The package and library name must have a hierarchical
    nomenclature, where the first name is the published/author identifier and the second (and following) names identify the library scope. For example, `Contoso.Conversion` is a library of conversion functions made by Contoso, whereas `Northwind.Math.Geometry` is a set of geometrical mathematical functions made by Northwind.  
4. **Function Naming**: All functions within the package should be prefixed with the package name to avoid naming conflicts. For example, if your package is named `Test.Functions`, a function named `Sum` should be named `Test.Functions.Sum`. Function names should also follow PascalCase conventions and the [DAX naming conventions for user-defined functions](https://docs.sqlbi.com/dax-style/dax-naming-conventions#user-defined-functions).
5. **Reserved Keywords**: Do not use `Dax.` in the name of the library (Dax as a single word is a reserved keyword in a function name). `DaxLib.` as a prefix is a reserved word for public open-source libraries of common use that are reviewed and approved by DaxLib maintainers. Do not create pull request for new `DaxLib.` libraries.
6. **Folder Structure**: The first level in the folder structure should be a single letter corresponding to the first letter of the package name (for example, a package `test.functions` will be in `/packages/t/test.functions/` folder). This is a technique used to reduce the number of elements in a single folder.
7. **Lowercase for Folders and Files**: All names of folders and files must be in lowercase; the name of the package (with uppercase letters if necessary) is defined in the metadata (`manifest.daxlib` file) of the package.  

By following these naming conventions, you help maintain a well-organized and easily navigable repository of DAX libraries, making it easier for users to find and utilize the functions they need.