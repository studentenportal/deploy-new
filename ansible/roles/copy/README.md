Copy
====

Copies files/directories recursivly to the host. Practice showed that
_Jinja 2_ cannot process binary files correctly.

### Pitfalls
1. The folder which src points to will not be copied, but it's childs
2. Role only templates files with the _.template_ ending and removes the ending
3. If file should be owned by root, explicit owner + group attributes needed
4. If mode is not given, the local file mode is taken for the file

Requirements
------------

None

Role Variables
--------------

| Name    | Default       | Value type                                 |
| --------|---------------|--------------------------------------------|
| src     | Required      | relative path in string from the playbook  |
| dest    | tmp Path      | absolute path in string on Remote          |
| delete  | no            | when yes deletes all files before copying  |
| mode    | 0640          | Octal Nbr UNIX File permissions            |
| owner   | user logged in| File owner like given to chown             |
| group   | user logged in| Owner posix group like given to chown      |
| mode    | src file mode | Access Control mode, Maybe 0777, u+rwx or u=rw,g=r,o=r |

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
                user: 'matt'
                group: 'matt'
                mode: 'u=rw,g=r,o=r'
```
