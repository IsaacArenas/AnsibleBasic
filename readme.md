# Ansible Playbook Basic Project Structure

Basic example on how to use an ansible playbook 

Things on this example:
 - roles
 - variables
 - ansible-vault variables
 - playbook
 - pre_tasks
 - post_tasks


how to execute 

```sh
#using a host group "cosa" and asking for the vault password 
$ ansible-playbook  "playbook.yml" --ask-vault-pass --extra-vars variable_host=cosa
#asking for the vault password (pasword is "pass")
$ ansible-playbook  "playbook.yml" --ask-vault-pass
#passing the vault password in a file 
$ ansible-playbook  "playbook.yml" --vault-password-file ~/.vault_pass.txt
```

to create the ansible-vault file 

```sh
#execute
$ ansible-vault create vars/vault-variables.yml
#insert the vault password (would be the one you use for the execution)
```
the content of the vault-variables.yml looks like this :

```yml
username: iarenas
password: fake123
```

using interpolation as part on the script we can use this variables like this :

```yml
  post_tasks:
    - name: Executing Post Tasks 1
      debug: msg="post tasks {{ username }}"

    - name: Executing Post Tasks 2
      debug: msg="post {{ password }}"
```
