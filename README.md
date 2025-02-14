# Repro for issue 8219

## Versions

firebase-tools: v13.31.1 - branch `jh-fix-import`<br>
node: v22.13.1

## Steps to reproduce

1. Run `firebase emulators:start --import saved_data --only dataconnect --project PROJECT_ID`

```
i  emulators: Starting emulators: dataconnect
⚠  emulators: It seems that you are running multiple instances of the emulator suite for project PROJECT_ID. This may result in unexpected behavior.
⚠  dataconnect: 'firebase.json#emulators.dataconnect.dataDir' is set and `--import` flag was passed. This will overwrite any data saved from previous runs.
? Do you wish to continue and overwrite data in dataconnect/.dataconnect/pgliteData? (y/N)

```

2. Answer with (Y)
   - Error is raised

```
[debug] [2025-02-14T18:24:40.001Z] Importing from /Users/USER_NAME/Desktop/firebase-tools/issues/8219/Users/USER_NAME/Desktop/firebase-tools/issues/8219/saved_data/dataconnect_export/postgres.tar.gz
[debug] [2025-02-14T18:24:40.002Z] Error: ENOENT: no such file or directory, open '/Users/USER_NAME/Desktop/firebase-tools/issues/8219/Users/USER_NAME/Desktop/firebase-tools/issues/8219/saved_data/dataconnect_export/postgres.tar.gz'
    at Object.openSync (node:fs:562:18)
    at Object.readFileSync (node:fs:446:35)
    at PostgresServer.getDb (/Users/USER_NAME/Desktop/firebase-tools/git-clone/firebase-tools/lib/emulator/dataconnect/pgliteServer.js:94:31)
    at process.processTicksAndRejections (node:internal/process/task_queues:105:5)
    at async Object.onMessage (/Users/USER_NAME/Desktop/firebase-tools/git-clone/firebase-tools/lib/emulator/dataconnect/pgliteServer.js:55:32)
[error]
[error] Error: An unexpected error has occurred.
```
