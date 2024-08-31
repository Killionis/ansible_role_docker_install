# README

This repository contains an Ansible playbook and role to install Docker on Ubuntu machines.

## Compatibility

The Ansible role is compatible with the following operating systems:

- Ubuntu Bionic (18.04)
- Ubuntu Focal (20.04)
- Ubuntu Jammy (22.04)

## Repository Structure

```
.
├── README.md               # Documentation of the repository
├── inventory
│   └── hosts               # Inventory file listing the target hosts
├── playbook.yml            # Main Ansible playbook
└── roles
    └── docker_install      # Ansible role for installing Docker
        ├── meta
        │   └── main.yml    # Metadata for the docker_install role
        └── tasks
            └── main.yml    # Main tasks for installing Docker
```

### Files and Directories

- **`inventory/hosts`**: The inventory file that lists the hosts where the playbook will be executed. You can specify different hosts or groups of hosts in this file.
- **`playbook.yml`**: The main playbook file that includes the Docker installation role.
- **`roles/docker_install/`**: The role directory containing tasks and metadata related to Docker installation.

## Prerequisites

- **Ansible**: Ensure that Ansible is installed on your control node (the machine from which you are running the playbook).
- **SSH Access**: You must have SSH access to the target hosts with the appropriate user and SSH key configured.

## Inventory Setup

Edit the `inventory/hosts` file to define your target hosts. Example:

```ini
[webservers]
webserver1.example.com ansible_user=your_user
webserver2.example.com ansible_user=your_user

[dbservers]
dbserver1.example.com ansible_user=your_user
dbserver2.example.com ansible_user=your_user
```

- **`ansible_user`**: Specify the SSH user to connect to each host.

## How to Use

1. **Clone the repository**:

   ```bash
   git clone <repository_url>
   cd <repository_directory>
   ```

2. **Edit the inventory file**:

   Update `inventory/hosts` to include the hosts where you want to install Docker.

3. **Run the playbook**:

   Execute the following command to run the playbook:

   ```bash
   ansible-playbook -i inventory/hosts playbook.yml
   ```

   This command will connect to the hosts listed in the inventory file and install Docker using the specified role.

## Playbook Explanation

The `playbook.yml` file is designed to install Docker on all hosts listed in the inventory. The playbook references the `docker_install` role, which contains tasks to:

- Add Docker's official GPG key.
- Set up Docker's apt repository.
- Install Docker packages (`docker-ce`, `docker-ce-cli`, `containerd.io`, etc.).

## Customization

If you need to customize the Docker installation (e.g., installing a specific version), you can modify the role's tasks in `roles/docker_install/tasks/main.yml`.

## Troubleshooting

- **Common Issues**: Ensure that your SSH configuration is correct and that the control node has network access to the target hosts.
- **Log Files**: Ansible will display output in the terminal during playbook execution, which can help identify any issues.

## License

This repository is licensed under the MIT License. See `LICENSE` for more information.


