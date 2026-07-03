# unzip-to-7z

A `7z`-based replacement for the `unzip` command.

## Why

The original `unzip` (Info-ZIP) has seen little development since 2009 and sometimes mangles non-ASCII filenames (e.g. `????.txt` for CJK characters). It remains the default on most systems, and many tools expect it to be present.

This wrapper uses `7z` under the hood to provide correct UTF-8 filename handling while maintaining a compatible command-line interface. Options are parsed and mapped based on `unzip` 6.0's `uz_opts()` logic.

## Installation

Ensure you already have the dependencies:
- `bash`
- `7z` (from `p7zip`)

Then just place the script `unzip` somewhere on your `$PATH`.

For most distros, you can do this by simply putting it under `/usr/local/bin/`:
```bash
sudo cp unzip /usr/local/bin/unzip
```

For NixOS you can add the following to your configuration, and remember to change `./unzip` to the actual path of the `unzip` script relative to the configuration file:
```
environment.systemPackages = [
  (pkgs.writeShellScriptBin "unzip" (builtins.readFile ./unzip))
];
```

Note: this script replaces the original `unzip`. If both are installed,
the one earlier in `$PATH` takes precedence.

## Usage

Same syntax as the original `unzip` (Info-ZIP unzip 6.0):

```bash
unzip -h                       # show help
unzip archive.zip              # extract
unzip -l archive.zip           # list files
unzip -p archive.zip file.txt  # output to stdout
```

## License

MIT License
