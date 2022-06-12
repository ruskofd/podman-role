Role Variables
--------------

#### Containers

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `podman_default_capabilities`     | see [defaults/main.yml](defaults/main.yml) | Defines the default capabilities that Podman must attach to containers by default |
| `podman_default_sysctls`          | see [defaults/main.yml](defaults/main.yml) | Defines the default sysctls that Podman must attach to containers by default |
| `podman_default_ulimits`          | `[]`                         | Defines the default ulimits that Podman must attach to containers by default |
| `podman_init_enabled`             | `false`                      | If set to `true`, Podman will attach a tiny init process in each container to reap zombie processes and forward signals by default |
| `podman_keyring_enabled`          | `true`                       | If set to `true`, tell Podman to create kernel keyring for use in containers |
| `podman_log_driver`               | `journald`                   | Defines the logging driver for containers. Possible values are `k8s-file` or `journald`. |
| `podman_log_size_max`             | `-1`                         | Defines maximum size allowed for the container log file. Negative numbers indicate that no size limit is imposed |
| `podman_log_tag`                  | `""`                         | Defines the default format tag for container log messages        |
| `podman_pids_limit`               | `2048`                       | Defines the maximum number of processes allowed in a container   |
| `podman_seccomp_profile_path`     | `/usr/share/containers/seccomp.json` | Defines the path to the SECCOMP profile policy to use for containers |
| `podman_userns_mode`              | `host`                       | Defines the User Namespace mode for containers. Possible values are `host` or `auto` |
| `podman_userns_size`              | `65536`                      | Defines the number of UIDs to allocate for the automatic container creation |
| `podman_userns_range`             | `1000000:1000000`            | Defines the UID/GID range required by Podman to run containers with User Namespace when using rootful containers |

#### Network

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `podman_network_backend`          | `netavark`                   | Defines the network backend to use for containers. Possible values are `netavark` or `cni` |
| `podman_network_default_name`     | `podman`                     | Defines the network name of the default network to attach pods to |
| `podman_network_default_subnet`   | `10.88.0.0/16`               | Defines the default subnet for the default network given in `podman_network_default_name` |

#### Engine

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `podman_cgroup_manager`           | `systemd`                    | Defines the cgroup management implementation used for the runtime. Possible values are `systemd` or `cgroupsfs` |
| `podman_events_logger`            | `journald`                   | Defines the logging mechanism to use for container engine events |
| `podman_runtime`                  | `crun`                       | Defines the default OCI runtime to use for containers            |


#### Registries

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `podman_unqualified_search_registries`| see [defaults/main.yml](defaults/main.yml) | Defines the list of registries to try when pulling an unqualified image |
| `podman_shortname_mode`           | `enforcing`                  | Defines the Short-Name aliasing mode to use when pulling images. Possible values are `enforcing`, `permissive` or `disabled`. More informations about this option [here](https://github.com/containers/image/blob/main/docs/containers-registries.conf.5.md#short-name-aliasing-modes) |

#### API

| Name                              | Default                      | Description                                                      |
| :-------------------------------- | :--------------------------- | :--------------------------------------------------------------- |
| `podman_api_enabled`              | `false`                      | If set to `true`, enable the Podman API service                  |
| `podman_api_activation_mode`      | `socket`                     | Defines how the Podman API should be activated. Two values are possible : `socket` and `service`. `socket` defines that the API must be started using systemd socket activation feature. `service` defines that the API service should be always enabled and started on boot using the systemd service. |
| `podman_api_timeout_sec`          | `5`                          | Defines the number of seconds to wait without a connection before the Podman API service times out and exits |

[Return to main page](../README.md)