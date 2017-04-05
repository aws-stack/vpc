Role Name
=========

Creates a VPC in your AWS account

Requirements
------------

Programmatic AWS access

Role Variables
--------------

This role uses one variable called stack, which is a dict containing:

    stack:
      name: my-app
      region: us-east-1
      env: prod
      vpc_cidr: 10.0.0.0/16

      subnets:

        web-a : 10.0.1.0/24
        data-b: 10.0.2.0/24
        file-a: 10.0.3.0/24
        util-a: 10.0.4.0/24

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------


    - hosts: localhost
      gather_facts: false
      connection: local

      vars_prompt:
        - name: stack_name
          prompt: What's the name of the stack to be launched?
          when: stack_name is undefined

      pre_tasks:
        - include_vars: "../stacks/{{ stack_name }}/main.yml"
          tags: [always]

      roles:
        - role: vpc
          tags: [always]


License
-------

BSD

Author Information
------------------

Filipe Niero Felisbino <filipenf@gmail.com>

