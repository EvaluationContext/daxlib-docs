---
layout:         page
title:          Contribute Medium-Large Libraries to DAX Lib
menu_title:     Medium-Large Libraries
published:      true
date:           2025-10-17
modified:       2025-10-17
order:          /04
next_reading:   true
---

You don’t have to create a repository for your DAX library on daxlib.org, but it’s a smart move if you expect the library to grow. A GitHub repo helps you track issues, accept contributions, and manage changes easily.

To create a GitHub repository for your DAX library, ensure you have a GitHub account; if not, create one. Then, follow the instructions at [https://github.com/daxlib/lib-quickstart-template](https://github.com/daxlib/lib-quickstart-template)

**TODO**

You can follow these steps to add a new package to DAX Lib:

1. **Create a name** for your package following the [naming conventions](naming-conventions.md) for both the name of the library and the package.

2. **Create the manifest** in `manifest.daxlib` file.
    
    The `manifest.daxlib` is a mandatory file contains the package properties in JSON format. You can see the [DaxLib.Sample](https://daxlib.org/package/DaxLib.Sample/#code) package for an example and refer to the [JSON schema](https://github.com/daxlib/daxlib/blob/main/schemas/manifest/1.0.0/manifest.1.0.0.schema.json) for the complete specification of available properties.

    The manifest file should be located in the root folder of the library:

    ```bash
    /manifest.daxlib
    ```

3. **Create the DAX user-defined functions** in `lib/functions.tmdl` and follow the [naming conventions](naming-conventions.md) for the function names.

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

4. **(Optional) Add a custom icon for your library**

    You can include a custom icon for your library by adding a PNG file inside the library's folder. 
    
    **Remarks**:
    - The icon file must be in PNG format (`.PNG`), with a maximum size of 100 KB.
    - Place the icon file at:

    ```bash
    /icon.png
    ```

    If you include a library icon, you must also update the `manifest.daxlib` to specify the file path.

    ```json
    {
      // ...other manifest properties...
      "icon": "/icon.png"
    }
    ```

5. **(Optional) Add a README file**

    You can include a README file to provide documentation for your library. It can include general information about the library, usage instructions, examples, and any notes for users.
    
    **Remarks**:
    - The file must be in Markdown format (`.MD`), with a maximum size of 100 KB.
    - For security reasons, only a limited set of Markdown features are supported, and external links may be restricted to trusted domains.

    Place the README file at:

    ```bash
    /README.md
    ```

    If you include a README file, you must also update the `manifest.daxlib` to specify the file path.

    ```json
    {
      // ...other manifest properties...
      "readme": "/README.md"
    }
    ```

6. **Create a pull request** to publish the library on [daxlib.org](https://daxlib.org/) following the instruction at [https://github.com/daxlib/lib-quickstart-template](https://github.com/daxlib/lib-quickstart-template?tab=readme-ov-file#-publish-your-library).
    - The pull request must be approved manually by DaxLib owners/maintainers.
    - When the pull request is approved, the package is immediately published.
