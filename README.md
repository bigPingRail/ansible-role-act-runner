# Ansible Role: Act-Runner

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This role installs and configures the act-runner.

## Requirements

- Ansible version 2.9 or higher.

## Supported Platforms

- Ubuntu:
  - yakkety
  - zesty
  - xenial
- Debian:
  - bookworm
  - bullseye

## Role Variables

Below are the available role variables, along with their descriptions:

- `act_runner_version`: The version of act-runner to be installed. (Default: `"0.2.6"`)
- `act_runner_token`: One time authentication token for act-runner. (Default: `""`)
- `act_runner_labels`: Comma separated labels/tags associated with the act-runner. (Default: `""`)
- `act_runner_name`: The name of the act-runner instance, which might be used to identify it uniquely among multiple runners. (Default: `""`)
- `act_runner_file`: The file path where act-runner's configuration or metadata is stored. (Default: `"/home/act-runner/.runner"`)
- `gitea_instance_url`: The URL of the Gitea instance with which the act-runner interacts. (Default: `""`)

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: true
  vars:
    act_runner_version: "0.2.6"
    act_runner_labels: "test,prod"
    act_runner_name: "production_runner"
    gitea_instance_url: "https://your.gitea.instance"
  roles:
    - act_runner
```

# Example Run 
```bash
ansible-playbook \
  --inventory inventory.yaml \
  --private-key ~/.ssh/id_rsa \
  --extra-vars act_runner_token="your_token_here" \
  --extra-vars act_runner_name="test" \
  ansible/playbook.yml
```

## Author Information

This role was created by [fmpanic@gmail.com](mailto:fmpanic@gmail.com).

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

