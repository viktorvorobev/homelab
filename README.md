# homelab

## Adguard

### HOWTO

1. Check interface name via `ip addr show`
2. Add interface to `docker-compose-adguard.yaml`
4. `make run-adguard` to create network and launch adguard container

> [!note]
> Current network configuration will put addguard to `192.168.0.225` address.
> The available address range is `192.168.0.225-192.168.0.230`

5. Setup bridge between macvlan and other network:
    - Create new macvlan interface:
        ```bash
        sudo ip link add mymacvlan link wlp0s20f3 type macvlan mode bridge
        ```
        > Host is the same from the step 1
    - Assign reserved IP address:
        ```bash
        sudo ip addr add 192.168.0.224/32 dev mymacvlan
        sudo ip link set mymacvlan up
        ```
    - Route IP range to this new interface
        ```bash
        sudo ip route add 192.168.0.224/29 dev mymacvlan
        ```
    - To undo all the above:
        ```bash
        sudo ip route del 192.168.0.224/29 dev mymacvlan
        sudo ip link set mymacvlan-shim down
        sudo ip addr delete 192.168.0.224/32 dev mymacvlan-shim
        sudo ip link delete mymacvlan link wlp0s20f3 type macvlan mode bridge
        ```
