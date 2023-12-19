# [snaps](#snaps)

## Description

Install snapd and install snaps on your system.

## Playbook

```yaml
#!/usr/bin/env ansible-playbook
---
- name: Playbook loclahost
  hosts: localhost
  become: yes
  gather_facts: yes
  roles:
    - role: cjsteel.snapd
      snapd_apps:
        - name: authy
          channel: latest/stable
        - name: vlc
          channel: latest/stable
        - name: upnote
          channel: latest/stable
          state: absent

## Other considerations

Other things to consider?

* [managing-ubuntu-snaps](https://www.freecodecamp.org/news/managing-ubuntu-snaps/)
* [codeberg.org/ansible/snapd](https://codeberg.org/ansible/snapd/src/branch/main/tasks/main.yml)

Update snap

```yaml
snap refresh core
```

Where is the snap config/directory

```yaml
- name: snapd config dir
  become: true
  file:
    path: "{{ snapd_config_path | dirname }}"
    state: directory

- name: configure snapd
  when: snapd_configuration is defined
  become: true
  template:
    src: snapd.conf.j2
    dest: "{{ snapd_config_path }}"
    mode: "u=rw,go=r"
  notify: restart snapd # ?
```


