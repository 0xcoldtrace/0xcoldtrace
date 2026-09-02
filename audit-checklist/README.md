# audit-checklist

Systematic checklist for smart contract security audits. Built from personal experience and known exploit patterns.

---

## pre-audit

- [ ] Read documentation and whitepaper
- [ ] Understand the protocol's economic model
- [ ] Identify all external dependencies (oracles, bridges, tokens)
- [ ] Map trust assumptions — who has admin keys, what can they do
- [ ] Check deployment config — upgradeable? timelock? multisig?

## access control

- [ ] All privileged functions have proper modifiers
- [ ] Role hierarchy is correctly implemented
- [ ] No unprotected initializers on upgradeable contracts
- [ ] Owner/admin cannot rug users (or there's a timelock)
- [ ] Two-step ownership transfer pattern used

## reentrancy

- [ ] CEI (Checks-Effects-Interactions) pattern followed
- [ ] Cross-function reentrancy: state shared between functions
- [ ] Cross-contract reentrancy: callbacks to other protocol contracts
- [ ] Read-only reentrancy: view functions returning stale state during callback
- [ ] ERC-777 / ERC-1155 callback vectors checked

## math & precision

- [ ] No division before multiplication
- [ ] Rounding direction favors the protocol
- [ ] No overflow/underflow in unchecked blocks
- [ ] Fee calculations handle edge cases (0 amount, dust)
- [ ] Share/asset ratio manipulation (first depositor attack)

## oracle & pricing

- [ ] Oracle staleness check (heartbeat timeout)
- [ ] Chainlink sequencer uptime check (L2)
- [ ] TWAP window sufficient (>30 min for volatile assets)
- [ ] Flash loan resistant pricing
- [ ] Graceful handling of oracle failure / zero price

## token integration

- [ ] Fee-on-transfer token support
- [ ] Rebasing token handling
- [ ] ERC-20 return value checked (SafeERC20)
- [ ] Token decimals != 18 handled correctly
- [ ] Blacklistable tokens (USDC/USDT) considered

## liquidation & debt

- [ ] Liquidation cannot be blocked by attacker
- [ ] Bad debt socialization mechanism exists
- [ ] No self-liquidation profit exploit
- [ ] Dust positions cannot brick the system

## upgradability

- [ ] Storage layout preserved between versions
- [ ] No selfdestruct in implementation
- [ ] Initializer called exactly once
- [ ] Gap slots reserved in base contracts

## cross-chain / bridges

- [ ] Message replay protection
- [ ] Source chain verification
- [ ] Handling of failed messages
- [ ] Gas limit estimation for destination execution

## general

- [ ] No front-running / sandwich opportunities in core flows
- [ ] Emergency pause mechanism exists
- [ ] Events emitted for all state changes
- [ ] No hardcoded addresses that could change
- [ ] Denial-of-service via unbounded loops

---

*this checklist evolves with every audit. it's a starting point, not a ceiling.*
