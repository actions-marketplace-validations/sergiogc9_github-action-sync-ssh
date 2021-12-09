# GitHub Action Sync SSH

A Github action to sync content to a remote server.

### Options

| Option             | Description                                                                                                                                | Type    | Default |            |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ | ------- | ------- | ---------- |
| `host`             | The server host.                                                                                                                           | string  |         | `required` |
| `port`             | The server port.                                                                                                                           | number  |         | `required` |
| `username`         | Username for authentication.                                                                                                               | string  |         | `required` |
| `password`         | Password for user authentication.                                                                                                          | string  |         | `required` |
| `local-directory`  | The local directory where files to be pushed are located..                                                                                 | string  |         | `required` |
| `remote-directory` | The remote directory in server where files will be pushed.                                                                                 | string  |         | `required` |
| `remove-content`   | Boolean to remove the existing content in destination directory. Be careful using this option together with a wrong destination directory. | boolean | `False` |            |

### Example usage

```yml
- name: Deploy React build
  uses: sergiogc9/github-action-sync-ssh@latest
  with:
    host: ${{ secrets.HOST }}
    port: ${{ secrets.PORT }}
    username: ${{ secrets.USERNAME }}
    password: ${{ secrets.PASSWORD }}
    local-directory: './build'
    remote-directory: '/home/user/web/react/'
```

### Development

To create a new version follow these steps:

1. Update and commit code.
2. Create a new build using `yarn build` and commit the `dist` folder.
3. Update version in package.json and commit with name as `Release VERSION`.
4. Create a new version tag using `git tag VERSION`.
5. Set created tag as `latest` tag using `git tag -f latest`.
6. Push tags with `git push --tags --force`.
7. Create a release using the github page.

### Credits

Built using [node-ssh](https://github.com/steelbrain/node-ssh).
