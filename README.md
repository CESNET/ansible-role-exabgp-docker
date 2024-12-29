# exabgp_docker

Role for setting up a docker running exabgp.
Configuration is done by the added files and templates(Not part of this role).

## Requirements

- Setting up network interfaces must be done before running this role.

## Role Variables

- exabgp_path - Base path where the files will be copied or created
- exabgp_dirs - List of directories which will be created (Path is relative to /)
  - Example value: `- { path: "{{ exabgp_path }}" }`
- exabgp_files - List of files which will be copied to machine
  - Example value: `- {src: "", dest: "", user: "", group: "", mode: ""}` where:
    - src - required
    - dest - optional; Default value: same as src; Relative to `exabgp_path`
    - user - optional; Default value: root
    - group - optional; Default value: root
    - mode - optional; Default value: 0644
- exabgp_templates - List of templates
  - Example value: `- {src: "", dest: "", user: "", group: "", mode: ""}` where:
    - src - required
    - dest - optional; Default value: same as src; Relative to `exabgp_path`
    - user - optional; Default value: root
    - group - optional; Default value: root
    - mode - optional; Default value: 0644
- exabgp_docker_compose_template - Name of the used docker-compose template
  - Relative to the folder with templates
- exabgp_custom_volumes - List of volumes connected to docker
  - Only for default docker_compose_template
  - Example value: `- "/etc/docker/data_volume:/data_volume"`
- exabgp_docker_image - Name of the docker image
  - Only for default docker_compose_template

## Dependencies

--

## Example Playbook

    - hosts: all
      roles:
         - cesnet.exabgp_docker

## Tags

- `exabgp` - Runs all task to create directories, copy files, create files from templates and run docker with ExaBGP
- `exabgp_start` - Try to start docker with ExaBGP
- `exabgp_stop` - Try to stop docker with ExaBGP
- `exabgp_restart` - Try to restart docker with ExaBGP

## Author Information

Pavel Vyskocil <Pavel.Vyskocil@cesnet.cz>.
