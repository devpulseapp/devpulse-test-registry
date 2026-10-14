# DevPulse add-on registry (test)

**Temporary test fixture.** This is the test copy of the signed list that tells DevPulse which published add-on releases its Marketplace offers. The real registry will be `devpulse-registry`; this one is deleted when the Marketplace goes live.

- `root/1.json`: the trust root, with the public keys and what each may sign. These are throwaway test keys.
- `publishers.json`, `revocations.json`: approved publishers and revoked add-ons.
- `widgets/`, `analyzers/`, `apps/`: one section per kind, each with `snapshot.json` (a table of contents), `listing/<n>.json` (for browsing) and `addons/<id>/<n>.json` (each version, its manifest and where its file is). Files the snapshot names carry their version in their path and are never rewritten, so a cache never mixes old and new files.

Every file is signed with OpenSSH (`ssh-keygen -Y sign`, namespace `devpulse-registry`) and maintained with the SDK's `devpulse-addon-registry` command, which checks the whole registry as DevPulse reads it before writing. The add-on files themselves stay in each publisher's GitHub Releases: [devpulse-test-widgets](https://github.com/devpulseapp/devpulse-test-widgets), [devpulse-test-analyzers](https://github.com/devpulseapp/devpulse-test-analyzers) and [devpulse-test-app-sample](https://github.com/devpulseapp/devpulse-test-app-sample).
