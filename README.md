# ansible_fedora_post_install
Install packages onto Fedora system via Ansible playbook

## Synopsis
This playbook will install packages via `dnf` onto a Fedora system.  It has been tested with Fedora 35 running on a AWS EC2 `t3a.small` instance.

## Playbook Details

1) Configure the [inventory.ini](inventory.ini) file.
* * Replace `w.x.y.z` with your own IP address
* * Set the `ansible_ssh_private_key_file` value
* * Set the `ansible_user` value
* * * **Note:** This user should be able to ssh into the remote system without having to be prompted to accept any ssh keys by using the `ansible_ssh_private_key_file` file mentioned above
2) Edit `fedora_packages.yml` to customize packages you want installed

## Execution
```shell
ansible-playbook -i inventory.ini fedora_packages.yml
```

## Post install
Verify package installation:
```shell
# to see the last 50 installed packages, change 25 to 50
sudo rpm -qa --last | head -25
```