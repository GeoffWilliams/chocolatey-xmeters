# chocolatey packaging for xmeters

* [Upstream](https://entropy6.com/xmeters/)

My first choco package so bear with me ;-)

## Packaging steps

Key adjustments needed:
* Author, description info 
* Remove unused vars (url64, etc)
* Checksums (see notes in scripts)

### 1. Template creation (for new packages - already done!)

```powershell
choco new xmeters `
    --automaticpackage `
    packageversion="'1.0.103.0'" `
    maintainername="'Geoff Williams'" `
    maintainerrepo="'https://github.com/GeoffWilliams/chocolatey-xmeters'" `
    installertype=exe `
    url="'https://entropy6.com/xmeters/downloads/XMetersSetup.exe'" `
    silentargs="'/quiet /install'"
```

### 2. Template adjustment (already done)

* xmeters/xmeters.nuspec

### 3. Script adjustments

* xmeters/tools/chocolateyinstall.ps1
* xmeters/tools/chocolateyuninstall.ps1

### 4. Run packaging

```powershell
choco pack
```

### 5. Test packaging

* RUN IN VM
* Share this directory with VM
* Must COPY the files to `c:\` or wont work
* `choco install -y xmeters --debug --verbose --source .\xmeters\`

### 6. Working? Then release it!

* `git tag ...`
* `choco push...`

### Next steps

Well the package works, great! Unfortunately xmeters doesnt work with Windows 11 so this is just a how-to-package-for-chocolatey repo