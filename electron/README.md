## Realm SDK for Electron: best practices

This sample code illustrates some of the best practices suggested for the MongoDB Realm JS SDK.

These include (but are not limited to):

- Use of `newRealmFileBehavior`  and `existingRealmFileBehavior` recommended policies
- Progress listener
- Handling of a client reset error, with code to recover objects added and/or updated client-side when Sync wasn't available
- Custom logging function
- How to write to a synced realm from both the renderer and main process. 
The `main.js` file is the Electron main process. The `renderer.js` is the Electron renderer process.
To sync changes to a remote realm, open a synced realm on the main process using the `Realm.open()` syntax. Then open a non-synced realm on the renderer process using the `new Realm()` syntax and set ``sync:true`` on the configuration object. This will allow writes from the renderer process to be synced by the realm on the main process.

## To run this application
- Create a MongoDB Realm application and enable Realm Sync
- Get the Javascript models for the Data Models tab, and substitute the `TestDataSchema` in `realmUtils.js` (or create a module to import)
- Replace the `"<Application ID>"` with your Realm app id in `realmUtils.js`
- Replace the `"<Partition Value>"` with the partition you want to sync with in `realmUtils.js`
- npm install
- npm run start

## NOTE

- Because of a [known issue](https://github.com/realm/realm-js/issues/3650) with Electron on the Windows platform, the version to use on the platform at this time must be at most 10.4.x, recent versions will fail
- As of Realm JS SDK 10.3.0, Node.js version 15 isn't supported, please use at most version 14 (see [the Github issue](https://github.com/realm/realm-js/issues/3670)). The issue has been solved in version 10.4.0 of the SDK.

