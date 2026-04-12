# grub-customizer

Ansible role to install [Grub Customizer](https://launchpad.net/grub-customizer) on Debian/Ubuntu systems.

## Requirements

- Debian or Ubuntu host
- `become: true` privileges (sudo)

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `grub_customizer_package_name` | `grub-customizer` | Package name to install via apt |

## Requirements

- Debian or Ubuntu host
- `become: true` privileges (sudo)
- `ubuntu_codename` fact must be set before the role runs (provided by `tasks/set_ubuntu_codename.yml` in pre_tasks)

## Notes

On Linux Mint, `ansible_facts.distribution_release` returns the Mint codename (e.g. `zena`) instead of the Ubuntu base codename (e.g. `noble`). The role uses the `ubuntu_codename` fact (set by `tasks/set_ubuntu_codename.yml`) to add the PPA with the correct codename via `apt_repository`. On Debian (no PPA support), the PPA step is skipped with `ignore_errors: true` and grub-customizer is installed from the default repository.

## Example Playbook

```yaml
- hosts: all
  become: true
  roles:
    - role: grub-customizer
```

## License

MIT

## Author

Varssos