# Common Commands

### Connecting to localhost

You can tell ansible to bypass ssh and use a "local" connection in both your playbooks and inventory file by specifying `ansible_connection=local`

{% code-tabs %}
{% code-tabs-item title="/etc/ansible/hosts" %}
```bash
[local]

    localhost ansible_connection=local

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Execute a playbook on a specific host

```bash
ansible-playbook --limit <host from hosts file> someplaybook.yaml
```



