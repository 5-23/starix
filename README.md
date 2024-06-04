# starix
the github-blog bot(use discord webhook)
<img width="701" alt="image" src="https://github.com/5-23/starix/assets/86705803/46674cac-f4ce-4c09-928f-a2498db0fc19">

## post-conv
```fish
upload(name): description
# or
post(name): description
```

## fix-conv
```fish
fix(name): description
```
## Starix.toml
```toml
# ur blog url
url="https://blog.5-23.dev/p/{starix.id}/"
# ur blog thumbnail url
thumb="https://blog.5-23.dev/p/{starix.id}/thumb.jpg"
# webhook bot name
name="Asta blog"
# profile url
avatar="https://avatars.githubusercontent.com/u/86705803?v=4"

[post]
content="@everyone `{starix.id}`가 올라왔어요!"
color="#00ff00"

[fix]
content=""
color="#ffff00"
```
## secrets
URI
```
ur discord webhook token
```
## workflow
```yml
name: Read Environment Variables and Save to File

on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: macos-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: download file
      run: |
        wget "https://f.5-23.dev/project/starix"
        chmod +x starix
    - name: run starix
      run: |
        sleep 120
        export URI="${{ secrets.URI }}"
        ./starix

```
