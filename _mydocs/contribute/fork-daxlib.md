---
layout:         page
title:          Contribute Small Libraries to DAX Lib
menu_title:     Small Libraries
published:      true
date:           2025-10-17
modified:       2025-10-17
order:          /03
next_reading:   true
---

For small libraries (a few functions), you can follow these steps to add a new package to DAX Lib:

1. **Fork** the DAX Lib repository [https://github.com/daxlib/daxlib/fork](https://github.com/daxlib/daxlib/fork).
    
    This creates a personal copy of the repository in your GitHub account.
    
    **Remarks**:

    Do not make changes directly on the `main` branch. Always create a separate branch for each change you want to make. For example, `add-my-package-version-1.0.0`. This keeps your work isolated until it's reviewed and approved.

2. **Create a folder** for your package in `/packages/` and follow the [naming conventions](naming-conventions.md) for both the folder structure and name.

    You can optionally use the [DaxLib.Sample](https://github.com/daxlib/daxlib/tree/main/packages/d/daxlib.sample/0.1.6) package as a starting point: copy it, rename it according to your library’s name, and then update its contents to match your library.

    Example: for a library named `Contoso.Conversion` with version `1.0.0`, the folder structure should be:

    ```bash
    /packages/c/contoso.conversion/1.0.0/
    ```
    
3. **Create the manifest** in `manifest.daxlib` file.
    
    The `manifest.daxlib` is a mandatory file contains the package properties in JSON format. You can see the [DaxLib.Sample](https://daxlib.org/package/DaxLib.Sample/#code) package for an example and refer to the [JSON schema](https://github.com/daxlib/daxlib/blob/main/schemas/manifest/1.0.0/manifest.1.0.0.schema.json) for the complete specification of available properties.

    Example: for a library named `Contoso.Conversion` with version `1.0.0`, the manifest file should be located at:

    ```bash
    /packages/c/contoso.conversion/1.0.0/manifest.daxlib
    ```

4. **Create the DAX user-defined functions** in `lib/functions.tmdl` and follow the [naming conventions](naming-conventions.md) for the function names.

    The file `lib/functions.tmdl` is a mandatory file and contains the source code of the DAX user-defined functions using the TMDL syntax. For an example, see the [DaxLib.Sample](https://daxlib.org/package/DaxLib.Sample/#code) package.
    
    **Remarks**:
    - The `functions.tmdl` file should contain only the function definitions without the `createOrReplace` command.
    - Optional: add comments describing the function and its parameters to improve readability and usability, as suggested in the [DAX naming convention](https://docs.sqlbi.com/dax-style/dax-naming-conventions#comments).
    - Each UDF must include the mandatory annotations: `DAXLIB_PackageId` and `DAXLIB_PackageVersion`.

        Example: for a library named `Contoso.Conversion` with version `1.0.0` the annotations should be:
        
        ``` text
        annotation DAXLIB_PackageId = Contoso.Conversion
        annotation DAXLIB_PackageVersion = 1.0.0
        ```

5. **(Optional) Add a custom icon for your library**

    You can include a custom icon for your library by adding a PNG file inside the library's folder. 
    
    **Remarks**:
    - The icon file must be in PNG format (`.PNG`), with a maximum size of 100 KB.

    Example: for a library named `Contoso.Conversion` with version `1.0.0`, place the icon file at:

    ```bash
    /packages/c/contoso.conversion/1.0.0/icon.png
    ```

    If you include a library icon, you must also update the `manifest.daxlib` to specify the file path.

    ```json
    {
      // ...other manifest properties...
      "icon": "/icon.png"
    }
    ```

6. **(Optional) Add a README file**

    You can include a README file to provide documentation for your library. It can include general information about the library, usage instructions, examples, and any notes for users.
    
    **Remarks**:
    - The file must be in Markdown format (`.MD`), with a maximum size of 100 KB.
    - For security reasons, only a limited set of Markdown features are supported, and external links may be restricted to trusted domains.

    Example: for a library named `Contoso.Conversion` with version `1.0.0`, place the README file at:

    ```bash
    /packages/c/contoso.conversion/1.0.0/README.md
    ```

    If you include a README file, you must also update the `manifest.daxlib` to specify the file path.

    ```json
    {
      // ...other manifest properties...
      "readme": "/README.md"
    }
    ```

7. **Create a pull request** to publish the library on [daxlib.org](https://daxlib.org/)

    - Go [here](https://github.com/daxlib/daxlib/pull/new) to create a new pull request from your forked repository to the official DAX Lib repository.
    - The pull request must be approved manually by DAX Lib owners/maintainers.
    - When the pull request is approved, the package is immediately published.
