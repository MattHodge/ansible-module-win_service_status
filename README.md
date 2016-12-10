# Ansible Module - win_service_status

This is an Ansible Windows module to get the status of a service.

<!-- TOC depthFrom:2 -->

- [Usage](#usage)
    - [On a service that exists](#on-a-service-that-exists)
    - [On a service that doesn't exists](#on-a-service-that-doesnt-exists)

<!-- /TOC -->

## Usage
The following are some usage examples.

### On a service that exists 

```yml
- name: get service status of a server that exists
  win_service_status:
    name: winrm
  register: existing_service_status

- name: debug result of service that exists
  debug:
    msg: "{{ existing_service_status }}"
```

The result will be the following:

```json
{
  "msg": {
    "changed": false,
    "win_service_status": {
      "caption": "Windows Remote Management (WS-Management)",
      "exists": true,
      "name": "WinRM",
      "path_name": "C:\\Windows\\System32\\svchost.exe -k NetworkService",
      "start_mode": "Auto",
      "start_name": "NT AUTHORITY\\NetworkService",
      "state": "Running"
    }
  }
}
```

### On a service that doesn't exists 

```yml
- name: get service status of a server that does not exists
  win_service_status:
    name: testservice
  register: non_existing_service_status

- name: debug result of service that does not exists
  debug:
    msg: "{{ non_existing_service_status }}"
```

The result will be the following:

```json
{
  "msg": {
    "changed": false,
    "win_service_status": {
      "exists": false
    }
  }
}
```
