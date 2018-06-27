Copy
====

Copies files/directories recursivly to the host. Practice showed that
_Jinja 2_ cannot process binary files correctly. This role circumvents
this bug by using the older copy syntax, which does not process the
files with _Jinja 2_.

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
