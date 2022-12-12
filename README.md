# Ansible playbook to setup a wireguard VPN

- Create a VM somewhere and add it to the [inventory](inventory.yml) and make sure you have ssh access to it.
- Make sure the [wireguard port](inventory.yml#L23) is open on the VM.
- Edit the `ansible_host` variable as that is used to setup the vpn.
- Add or remove peers (vpn clients) using the [wireguard_peers](inventory.yml#L29) as necessary.
- Run the playbook: `ansible-playbook -i inventory.yml playbook.yml`.
- Once the playbook is done, all client configs should be present in the [config](inventory.yml#L38) directory.
- Download the wireguard app on your device and profit.

## Known Issues

- Sometimes I need to run `sudo ip addr flush dev eth0` if I get `RTNETLINK answers: File exists` error.
  - https://raspberrypi.stackexchange.com/questions/13895/solving-rtnetlink-answers-file-exists-when-running-ifup
- Hex math for ipv6 in `helpers.j2` is incorrect.
- If you want to add exclusions to traffic, replace the `AllowedIPs` part of `client.conf.j2`. You can use the following tool to calculate it:
  - https://www.procustodibus.com/blog/2021/03/wireguard-allowedips-calculator/
