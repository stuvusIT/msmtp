# msmtp

This role installs and configures msmtp for sending mail from the command line.

## Requirements

Ubuntu

## Role Variables

| Name             | Default / Mandatory | Description                                                                              |
|:-----------------|:-------------------:|:-----------------------------------------------------------------------------------------|
| `msmtp_defaults` | `{}`                | Key-Value dict of msmtp configuration items                                              |
| `msmtp_accounts` | `{}`                | Name-Values dict of msmtp accounts. See below for possible values                        |
| `msmtp_aliases`  | `{}`                | Local-Remote dict of msmtp aliases. The remote end may be a list for multiple recipients |

### Accounts

| Name      | Default / Mandatory | Description                                                 |
|:----------|:-------------------:|:------------------------------------------------------------|
| `parents` |                     | List of parent accounts this account inherits settings from |

All other options are directly fed directly to the corresponding msmtp account section.

## Example Playbook

```yml
- hosts: mail-senderes
  roles:
    - role: msmtp
      msmtp_defaults:
        auth: "on"
        tls: "on"
        tls_trust_file: /etc/ssl/certs/ca-certificates.crt
      msmtp_accounts:
        default:
          host: mail.example.com
          port: 587
        private:
          user: jdoe-private
          password: secret
        work:
          parents: private
          user: jdoe
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
