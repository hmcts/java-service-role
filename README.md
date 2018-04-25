# Ansible role to install Java services

An Ansible role for deploying and configuring executable jar based Java services.

## Requirements

None

## Role Variables

Java services are defined as a list in the `java_apps` variable.

```yaml
java_apps:
  - name: example
    user: example
    config_template: "templates/example/config.yml.j2"
    jar_src_path: "/var/lib/jenkins/something/example.jar"
    java_opts: "-XX:HeapDumpPath=/var/log/${log_path}/"
    enabled: true
    check: true
    app_type: "DROPWIZARD"
    dropwizard_migrate_database: true
    check_url: "http://localhost:8080/healthcheck"
    check_status: "400" # defaults to 200
```

### Limiting deployment

Deployment can be limited to a single java app by setting the `java_service_name` variable to the
name field of the java app to deploy.

```
ansible-playbook playbook.yml -e 'java_service_name=example'
```

### Extra details

`java_app.dropwizard_migrate_database`: if set to `true` run the `db migrate` dropwizard command


## Author Information

HMCTS Divorce Team
