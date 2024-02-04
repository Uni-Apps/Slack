If you include this role at top of your 'roles:' list, It will skip installing locally & install in Distrobox instead!

Use a conditional for each role to make them compatible with this:

role/{ role_name }/tasks/main.yml
```
- name: OS specific
  include_tasks: '{{ ansible_os_family }}/main.yml'
  when: ( in_container is not defined ) or ( ansible_env.container is defined )
```