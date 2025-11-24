<!-- action-docs-header source="action-file.yml" -->
<!-- action-docs-description source="action-file.yml" -->
Test
---

### Usage Example
Place the following in `/.github/workflows/main.yml`
```yml
on: push
name: 🚀 Deploy website on push
jobs:
  web-deploy:
    name: 🎉 Deploy
    runs-on: ubuntu-latest
    steps:
    - name: 🚚 Get latest code
      uses: actions/checkout@v4
    
    - name: 📂 Sync all files
      uses: pablo-schmeiser/SMB-Deploy-Action@v0.0.1
      with:
        smb_server: smb.pablo-schmeiser.com
        smb_share: mySmbShare
        smb_username: ${{ secrets.smb_username}}
        smb_password: ${{ secrets.smb_password }}

    - name: 📂 Sync index only
      uses: pablo-schmeiser/SMB-Deploy-Action@v0.0.1
      with:
        smb_server: smb.pablo-schmeiser.com
        smb_share: mySmbShare
        smb_username: ${{ secrets.smb_username}}
        smb_password: ${{ secrets.smb_password }}
        source_path: index.html
```

---
### Requirements
- You must have access to your SMB share on your server.
---

### Setup Steps
1. Select the repository you want to add the action to
2. Select the `Actions` tab
3. Select `Blank workflow file` or `Set up a workflow yourself`, if you don't see these options manually create a yaml file under `Your_Project/.github/workflows/main.yml`
4. Paste the example above into your yaml file and save.
5. Now you need to add a password and a username to the `secrets` section in your project. To add a `secret` go to the `Settings` tab in your project then select `Secrets`. Add a new `Secret` for `smb_password` and for `smb_username`
6. Update your yaml file settings
7. If you appreciate this github action give it a :star: or show off with one of the [badges below](#badge).

---

### Settings
Keys can be added directly to your .yml config files or referenced from your projects `Secrets` storage.

I strongly recommend you store your `smb_password` and your `smb_username` as a secret.
<!-- action-docs-inputs source="action-file.yml" -->

### Common Examples
#### Build and Publish prebuilt websites

#### Publish prebuilt PDFs

---
<!-- action-docs-runs source="action-file.yml" -->
---

## Badge
If you appreciate this github action give it a :star: or show off with one of the badges below. Feel free to edit the text or color.

[<img alt="Deployed with SMB Deploy Action" src="https://img.shields.io/badge/Deployed With-SMB DEPLOY ACTION-%3CCOLOR%3E?style=for-the-badge&color=0077b6">](https://github.com/pablo-schmeiser/SMB-Deploy-Action)

```md
[<img alt="Deployed with SMB Deploy Action" src="https://img.shields.io/badge/Deployed With-SMB DEPLOY ACTION-%3CCOLOR%3E?style=for-the-badge&color=0077b6">](https://github.com/pablo-schmeiser/SMB-Deploy-Action)
```

---

## FAQ

<details>
  <summary>How do I set a upload timeout?</summary>

github has a built-in `timeout-minutes` option, see customized example below

```yaml
on: push
name: Publish
jobs:
  deploy:
    name: deploy
    runs-on: ubuntu-latest
    timeout-minutes: 15 # time out after 15 minutes (default is 360 minutes)
    steps:
      ...
```
</details>

## Debugging your config locally
This action is a basic wrapper around my `@pablo-schmeiser/SMB-Deploy-Action` repository. To test your config you can install [@pablo-schmeiser/SMB-Deploy-Action](https://github.com/pablo-schmeiser/SMB-Deploy-Action) and then convert your config to a yml action. Settings are one-to-one, this action is only a wrapper.

## Contributing to this project
To test this action locally you will need to setup **docker** and **act** to run a environment similar to the one github uses for actions.
- Download/install docker, make sure it is running.
- install [act](https://github.com/nektos/act)
- Clone the [@pablo-schmeiser/SMB-Deploy-Action](https://github.com/pablo-schmeiser/SMB-Deploy-Action) git repository.
- **TODO:** Further steps are WIP
