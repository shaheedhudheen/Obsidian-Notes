


# Semantic Versioning

`Versions` of the npm packages in the dependencies section of your package.json file follow what’s called Semantic Versioning (SemVer)

an industry standard for software versioning aiming to make it easier to manage dependencies. Libraries, frameworks or other tools published on npm should use SemVer in order to clearly communicate what kind of changes projects can expect if they update.

```json
"package": "MAJOR.MINOR.PATCH"
```

The MAJOR version should increment when you make incompatible API changes. 

The MINOR version should increment when you add functionality in a backwards-compatible manner. 

The PATCH version should increment when you make backwards-compatible bug fixes.

This means that PATCHes are bug fixes and MINORs add new features but neither of them break what worked before. Finally, MAJORs add changes that won’t work with earlier versions.

# Tilde-Character to Always Use the Latest Patch Version of a Dependency

To allow an npm dependency to update to the latest PATCH version, you can prefix the dependency’s version with the tilde (`~`) character.

```json
"package": "~1.3.8"
```

# Caret-Character to Use the Latest Minor Version of a Dependency

the caret (`^`) allows npm to install future updates as well. The difference is that the caret will allow both MINOR updates and PATCHes.

```json
"package": "^1.3.8"
```

