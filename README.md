# ThemeBleed
Proof-of-Concept for CVE-2023-38146 ("ThemeBleed")
```
Usage: ThemeBleed.exe <command>

Commands:
        server                                   - Runs the server
        make_theme <host> <output path>          - Generates a .theme file referencing the specified host
        make_themepack <host> <output_path>      - Generates a .themepack file referencing the specified host
```

## Data files
The binaries in data correspond to the 3 files returned to the target by the PoC.
- `stage_1` - An `msstyles` file with the `PACKTHEM_VERSION` set to 999.
- `stage_2` - A valid unmodified `msstyles` file to pass the signature check.
- `stage_3` - The DLL that will be loaded and executed. The provided example simply launches `calc.exe`.

To make your own payload, create a DLL with an export named `VerifyThemeVersion` containing your code, and replace `stage_3` with your newly created DLL.
