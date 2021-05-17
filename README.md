# ansible-role-containerd

An Ansible Role that installs [containerd](https://containerd.io) on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

```bash
containerd_package: containerd.io
containerd_package_state: present
```

Package name and state controls.

```yaml
containerd_service_state: started
containerd_service_enabled: true
```

Service controls. You can install containerd but not have it running or enabled on boot by changing these defaults.

```yaml
containerd_config_default_write: true
```

Write containerd defaults to the containerd config.toml file.

```yaml
docker_apt_release_channel: stable
docker_apt_arch: amd64
docker_apt_repository: "deb [arch={{ docker_apt_arch }}] https://download.docker.com/linux/{{ ansible_distribution | lower }} {{ ansible_distribution_release }} {{ docker_apt_release_channel }}"
docker_apt_ignore_key_error: true
docker_apt_gpg_key: https://download.docker.com/linux/{{ ansible_distribution | lower }}/gpg
```

Apt installation paramemeters, useful if you want to switch from the stable channel releases, or install on a different CPU architecture (e.g. `arm64`).

```yaml
docker_yum_repo_url: https://download.docker.com/linux/{{ (ansible_distribution == "Fedora") | ternary("fedora","centos") }}/docker-ce.repo
docker_yum_repo_enable_nightly: '0'
docker_yum_gpg_key: https://download.docker.com/linux/centos/gpg
```

Yum/DNF installation parameters, useful if you want to switch from the stable repository.

## Dependencies

None.
