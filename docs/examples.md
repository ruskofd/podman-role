Configuration examples
----------------------

### Podman API

You have two options to start and use the Podman API. You can start it using systemd socket activation feature, and therefore the API service will start when requests on the UNIX socket occurs (`/run/podman/podman.sock`). The other option is to start API service normally on boot like any other services on the system.

* **Socket activated API service**

  ```YAML
  podman_api_enabled: true
  podman_api_activation_mode: socket

  # You can also defines the timeout before the API service exits if there is no connection on the socket. A value of '0' disable this timeout.
  podman_api_timeout_sec: 5
  ```

* **Standard API service (persistent service)**

  ```YAML
  podman_api_enabled: true
  podman_api_activation_mode: service
  podman_api_timeout_sec: 0
  ```

You can therefore check the connectivity to the API :

```JSON
$ curl -s --unix-socket /run/podman/podman.sock http://d/v4.0.0/libpod/containers/json | jq
[
  {
    "AutoRemove": false,
    "Command": [
      "nginx",
      "-g",
      "daemon off;"
    ],
    "Created": "2022-06-12T16:30:44.231126499+02:00",
    "CreatedAt": "",
    "Exited": false,
    "ExitedAt": -62135596800,
    "ExitCode": 0,
    "Id": "4d738b210774e0e3f743ca399f1975ef2b6c9f8ef15f2bc9817a110f6718b239",
    "Image": "docker.io/library/nginx:latest",
    "ImageID": "0e901e68141fd02f237cf63eb842529f8a9500636a9419e3cf4fb986b8fe3d5d",
    "IsInfra": false,
    "Labels": {
      "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
    },
    "Mounts": [],
    "Names": [
      "dazzling_vaughan"
    ],
    "Namespaces": {},
    "Networks": [
      "podman"
    ],
    "Pid": 864,
    "Pod": "",
    "PodName": "",
    "Ports": [
      {
        "host_ip": "",
        "container_port": 80,
        "host_port": 80,
        "range": 1,
        "protocol": "tcp"
      }
    ],
    "Size": null,
    "StartedAt": 1655044244,
    "State": "running",
    "Status": ""
  }
]
```