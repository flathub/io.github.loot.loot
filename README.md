# LOOT

## Updating to a new version of LOOT

1. In LOOT's [repository](https://github.com/loot/loot), run the `scripts/generate_manifests.sh` script (on Linux or in WSL).
2. Copy the JSON files it generates in `build/flatpak-manifests` to the `manifests` directory in this repository, replacing the existing files.
3. Copy the `resources/linux/io.github.loot.loot.yml` file from the LOOT repository to this repository.
4. In the copied YAML file, replace the `LOOT` module's `dir` source with a `git` source with the `url` of the LOOT Git repository and the relevant Git tag name.

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
      - type: git
        url: https://github.com/loot/loot.git
        tag: 0.23.0
    ```
5. In the copied YAML file, replace all instances of `../../build/flatpak-manifests/` with `manifests/`.
6. Commit the changes.
7. Open a pull request for the changes.
8. Once Flathub has built a test version, test it out. If it works, merge the pull request.
