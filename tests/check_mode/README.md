# Check Mode Tests for sap_ha_pacemaker_cluster

## Overview

Tests role variable construction and config generation without requiring actual infrastructure.

## Running Tests

### Prerequisites

```bash
ansible-galaxy collection install fedora.linux_system_roles:==1.25.4
```

### Run single test

```bash
cd tests/check_mode
ansible-playbook -i inventory/aws_hana_2node \
  test_rhel9_aws_hana_scaleup.yml \
  --check
```

### Verify generated config

```bash
cat /tmp/rhel9_aws_hana_config.yml
```

## Test Scenarios

- `test_rhel9_aws_hana_scaleup.yml` - RHEL 9 + AWS + HANA scaleup
- `test_sles15_aws_hana_scaleup.yml` - SLES 15 + AWS + HANA scaleup

## What Gets Tested

✅ Platform detection (AWS)
✅ OS-specific variable loading
✅ HANA resource construction
✅ STONITH configuration (fence_aws)
✅ VIP resource creation
✅ Constraint generation
✅ Config varfile generation

## Limitations

❌ No actual cluster creation
❌ No idempotence testing
❌ No file system operations
