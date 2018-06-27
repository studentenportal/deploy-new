Copy
====

Copies files/directories recursivly to the host. It also templates the
files with Jinja 2 template-syntax.

Requirements
------------

None

Role Variables
--------------

| Name    | Default       | Value type                                 |
| --------|---------------|--------------------------------------------|
| src     | Required      | relative path in string from the playbook  |
| dest    | tmp Path      | absolute path in string on Remote          |
| delete  | !dest defined | when yes deletes all files before copying  |
| mode    | 0640          | Octal Nbr UNIX File permissions            |

This role returns:

| Name     | Only If        | Value type              |
| ---------|----------------|-------------------------|
| tmpfolder| Undefined dest | String abs. path to dir |

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: servers
    - tasks:
         - name: Copies file/dir onto server
           import_role: name=copy private=yes
           vars:
                src: 'relative/path/to/file|dir/from/playbook/directory'
                dest: 'absolute/path/to/root/directory/'
```
