# fil-release data: mainnet

Snapshot of every Filecoin **mainnet** miner with locked funds, for the
[fil-release](https://github.com/dire-states/filecoin-fil-release) site, served at
`https://dire-states.github.io/filecoin-fil-release-data-main/`.

GitHub holds only the latest snapshot, as a single commit that each publish replaces. The full
history (one commit per snapshot) is kept locally on the machine that runs the fetch.

## Files

- `dataset.json`: marks this repo as the `mainnet` dataset. The fetch script refuses to write data
  from another network into it.
- `miners.json`: the overview index, loaded first by the site. Per miner: locked amounts, the next
  unlock and releases in the next 30 days. Network totals of daily releases.
- `miners/<id>.json`: one file per miner, loaded when the miner is selected. The vesting schedule,
  daily pledge releases, and exact balances in attoFIL.

See `MinerIndex` / `MinerData` in `src/lib/types.ts` of the app repo.

## Updating

From the app repo (uses the local mainnet node; `LOTUS_API` overrides):

```sh
scripts/publish.sh mainnet
```
