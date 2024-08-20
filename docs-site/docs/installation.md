# Installation

Download the latest release, that meets your platform, from the [releases page](https://github.com/aimotrens/impulsar/releases/latest) and extract it to a directory in your PATH.

## Windows

```powershell
$VERSION = "vX.X.X" # Replace with the latest version

Invoke-WebRequest `
    -Uri "https://github.com/aimotrens/impulsar/releases/download/$VERSION/impulsar_windows_amd64.zip" `
    -OutFile "impulsar_windows_amd64.zip"

Expand-Archive `
    -Path .\impulsar_windows_amd64.zip `
    -DestinationPath .

Move-Item -Path impulsar.exe -Destination {an directory in your PATH}
```

Or simply with winget:

```powershell
winget install impulsar
```

## Linux

```bash
VERSION="vX.X.X" # Replace with the latest version

curl -L -o impulsar_linux_amd64.tar.xz \
    https://github.com/aimotrens/impulsar/releases/download/$VERSION/impulsar_linux_amd64.tar.xz

tar -xvf impulsar_linux_amd64.tar.xz

mv impulsar {an directory in your PATH}
```

# JSON Schema
The impuslar repository provides a [JSON schema](https://github.com/aimotrens/impulsar/blob/main/schema.json) file. You can setup up this file in most popular IDEs and benefit from suggestens.
