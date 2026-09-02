# security-toolkit

Custom tools and scripts for smart contract security research.

---

## tools

### `reentrancy-scanner/`
Static analysis script that detects cross-function and cross-contract reentrancy patterns in Solidity codebases. Goes beyond Slither's default detectors.

```bash
python3 reentrancy_scan.py --target ./src --depth 3
```

### `oracle-checker/`
Checks for common oracle manipulation vectors — stale price feeds, TWAP window too short, missing circuit breakers, single-source dependency.

```bash
python3 oracle_check.py --contract 0x... --chain mainnet
```

### `access-control-map/`
Generates a permission map of all privileged functions in a protocol — who can call what, through which path, with what timelock.

```bash
python3 acl_map.py --src ./src --output map.json
```

### `storage-layout-diff/`
Compares storage layouts between proxy implementation upgrades. Catches storage collision before it hits mainnet.

```bash
forge inspect OldImpl storage-layout > old.json
forge inspect NewImpl storage-layout > new.json
python3 storage_diff.py old.json new.json
```

### `gas-griefing-detector/`
Identifies functions vulnerable to gas griefing — unbounded loops, external calls in loops, missing gas caps on callbacks.

---

## setup

```bash
git clone https://github.com/0xcoldtrace/security-toolkit.git
cd security-toolkit
pip install -r requirements.txt
```

## dependencies

- Python 3.10+
- Foundry
- Slither
- solc (multiple versions via solc-select)

---

*tools are built from patterns found during real audits. contributions welcome.*
