# Versioning

- Each artifact will have a unique ID
  - Can be taken from the CI tool.
- Make sure assemblies version have changed as well for each artifact
  - The assemblies version will be included in the Logs of the application, so we could blame a specific version.
  - As blaming a specific version, we truly want to blame a specific source control commit so we can blame some specific lines of code.
  - Thus we should increase all assemblies in the same repo to the same version for each commit, even though some assemblies in the repo didn't modify.
