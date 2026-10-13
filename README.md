# tool-releases

This repository holds release files only.
The source code of the tools is private.
The client tools that read this repository are not here.

## The manifest

The file `latest.json` is the list of tools. It gives the newest version of each tool.
For each tool it gives the download address and the SHA-256 digest of each file.
The format is defined in the repository `cardoskydweller/toolmanifest`.

## Targets

- `aarch64-apple-darwin`: a Mac with an Apple chip.
- `x86_64-unknown-linux-musl`: a Linux machine with an x86-64 processor.
- `any`: a script. It runs on all machines that have its interpreter.

## How to download one tool and verify it

1. Open `latest.json`. Find the tool and your target.
2. Download the file from the `url` of the asset:

   ```sh
   curl -fsSL -o fleet <url>
   ```

3. Calculate the digest of the file:

   ```sh
   shasum -a 256 fleet
   ```

4. Compare the result with the `sha256` of the asset in `latest.json`.
5. If the two values are different, delete the file. Do not run it.
6. Make the file executable:

   ```sh
   chmod +x fleet
   ```

## The easy way

The command `tools update` does these steps for you.
It reads `latest.json`, downloads the files, and checks the digests.
