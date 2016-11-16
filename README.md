
# kompose-install-role

Use to download and unarchive the latest [kompose](https://github.com/kubernetes-incubator/kompose) release asset for your OS.

## Requirements

- Accesses the GitHub API to find the release and it's assets, so you'll need internet access.
- Run with *gather_facts: yes*, if you want it to determine which asset to download based on the host's OS family. Or, you can set *kompose_asset_name* to the name of the desired asset.

## Role Variables

kompose_github_user: kubernetes-incubator
> Name of GitHub user that owns the kompose repo. Presumably it won't always be in the incubator.

kompose_github_name: kompose
> Name of the *kompose* repo. This likely won't change, but you never know.

kompose_github_url: https://api.github.com/repos
> The GitHub API URL.

kompose_asset_name: defaults based on OS 
> The specific asset you want to download. When ansible_os_family is *Darwin* (applies to OSX) will download *kompose_darwin-amd64.tar.gz*. When *Debian* or *RedHat* will download *kompose_linux-amd64.tar.gz *
kompose_release_id: 
> Provide the id of a specific release, otherwise the latest release will be downloaded.

kompose_release_tag_name:
> Provide a specific release tag name, otherwise the latest release will be downloaded.

kompose_dest: /usr/bin/kompose
> Destination directory where the binary should be placed.

## Dependencies

None

## Example Playbook

```
- hosts: localhost
  connection: local
  gather_facts: yes
  roles:
    - role: chouseknecht.kompose-install-role
      kompose_dest: "{{ lookup('env', 'HOME') }}/kompose"
```

## License

[Apache v2](http://apache.org/licenses/LICENSE-2.0)

## Author

[chouseknecht](https://github.com/chouseknecht)

