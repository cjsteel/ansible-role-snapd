Installation
=========
To use this Ansible role skeleton, as [described in Ansible Galaxy documentation](https://docs.ansible.com/ansible/latest/reference_appendices/galaxy.html#using-a-custom-role-skeleton):

```
ansible-galaxy init --role-skeleton=skeleton role_name
mv role_name ansible-role-role_name
cd ./ansible-role-role_name/
rm INSTALL.md
```

or add this to ansible.cfg:

```
[galaxy]
role_skeleton = /path/to/skeleton
role_skeleton_ignore = ^.git$,^.*/.git_keep$
```

Followed by `ansible-galaxy init role_name`.

Don't include `ansible-role` to the role name, for example use `java` instead of `ansible-role-java`.

ansible-skeleton-template

## Skeleton Customizations

Notes on further customizations to the role skeleton customizer.

You will need to ensure that Jinja2 template variables for the role name as well as Jinja2 reserved characters are escaped. See the flowing documentation for details on how to do this:

* [https://jinja.palletsprojects.com/en/3.0.x/templates/#escaping
