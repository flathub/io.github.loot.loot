# LOOT

## Updating to a new version of LOOT

1. In LOOT's [repository](https://github.com/loot/loot), run the `scripts/generate_manifests.sh` script (on Linux or in WSL).
2. Copy the JSON files it generates in `build/flatpak-manifests` to the `manifests` directory in this repository, replacing the existing files.
3. Copy the `resources/linux/io.github.loot.loot.yml` file from the LOOT repository to this repository.
4. In the copied YAML file, replace the `LOOT` module's `dir` source with a `file` source with the `url` of the `tar.gz` source code archive for the relevant LOOT release/tag/commit and the corresponding `sha256` value.

    E.g. replace the bit that looks like:

    ```yaml
        - type: dir
            path: ../..
            skip:
            - .github
            - build
    ```

    with something that looks like:

    ```yaml
        - type: file
            url: https://github.com/loot/loot/archive/refs/tags/0.22.4.tar.gz
            sha256: a7cf30ed89bb84d3d6843f121cedb528720403bda1b08b816f338cbae7cc5f8e
    ```
5. Commit the changes.
6. Open a pull request for the changes.
7. Once Flathub has built a test version, test it out. If it works, merge the pull request.
