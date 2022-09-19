# Ansible playbook to setup a wireguard VPN

- Create a VM somewhere and add it to the [inventory](inventory.yml) and make sure you have ssh access to it.
- Make sure the [wireguard port](inventory.yml#L23) is open on the VM.
- Edit the `ansible_host` variable as that is used to setup the vpn.
- Add or remove peers (vpn clients) using the [wireguard_peers](inventory.yml#L29) as necessary.
- Run the playbook: `ansible-playbook -i inventory.yml playbook.yml`.
- Once the playbook is done, all client configs should be present in the [config](inventory.yml#L38) directory.
- Download the wireguard app on your device and profit.
