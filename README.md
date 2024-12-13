# ansible-report
ansible report repository

Run with `ansible-playbook inventory_report.yml`








# Modifying API requests to Ansible Automation Platform

Here is an example Ansible task talking to the inventory on AAP ->

```
    - name: Retrieve job template list for each inventory and store in a dictionary
      ansible.builtin.uri:
        url: "https://{{ automation_controller_host }}/api/v2/job_templates/?inventory_id={{ inventory_id_var }}"
        method: GET
        user: "{{ controller_username }}"
        password: "{{ controller_password }}"
        force_basic_auth: true
        validate_certs: "{{ verify_ssl }}"
        return_content: true
```

### Return all jobs from specific inventory

```
api/v2/jobs/?inventory_id=10
```

### Return all jobs from specific inventory and created by a specific user

```
api/v2/jobs/?inventory_id=10&created_by=42
```

### Return all jobs from specific inventory and the job template was from a specific project (git repo)

```
api/v2/jobs/?inventory_id=10&project=347
```