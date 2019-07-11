[![Codacy Badge](https://api.codacy.com/project/badge/Grade/9207c14ad7414968a270f6085e8d1e59)](https://app.codacy.com/app/wuan/netboot-config?utm_source=github.com&utm_medium=referral&utm_content=Uniscon/netboot-config&utm_campaign=Badge_Grade_Dashboard)
[![Build Status](https://travis-ci.org/Uniscon/netboot-config.svg?branch=master)](https://travis-ci.org/Uniscon/netboot-config)
[![Coverage Status](https://coveralls.io/repos/github/Uniscon/netboot-config/badge.svg?branch=master)](https://coveralls.io/github/Uniscon/netboot-config?branch=master)

# netboot-config

Automated generation of KIWI image boot 

## Basic Usage

```
netboot-config netboot-config.yml
```

converts a YAML file in the following format

```yaml
hostgroups:
  - cidr: 10.0.11.0/24
    prefix: abc11
    hosts:
      - image_type: type1
        offset: 10
        count: 2
      - image_type: type2
        offset: 20
        config:
          - source: src
            target: tgt
hosts:
  - cidr: 10.0.10.0/24
    prefix: abc10
    hosts:
      - offset: 5
        alias: netboot
      - offset: 20
        count: 2
      - offset: 30
        alias: foo
      - offset: 40
        aliases:
          - bar
          - baz
```

to configuration files usable for KIWI network boot:

```
.
├── abc1110
│   └── hostname
├── abc1111
│   └── hostname
├── abc1120
│   └── hostname
├── config.0A000B0A
├── config.0A000B0B
├── config.0A000B14
├── config.default
└── hosts
```