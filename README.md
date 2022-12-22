## firebase-action

A composite action that installs `firebase-tools` from [firebase.tools](https://firebase.tools) and sets up
the credentials by way of a service account. This does not require nodejs or npm.

The result of installing the `firebase` command will be cached to speed up next workflow runs. The action will check if the latest version of `firebase`
is installed, and upgrade if this is not the case. Sending analytics is disabled using the `analytics=false` option.

## How to use in your workflow

Include the action, passing the json service account secret (just paste the json text as a Github Actions secret).
The `serviceAccount` parameter can be omitted, for example if you are using the `firebase` command for running emulators and such.

      - name: Setup Firebase
        uses: littlerobots/firebase-action@v1
        with:
          serviceAccount: ${{ secrets.MY_FIREBASE_SERVICE_ACCOUNT }}
          
     # somewhere later in your workflow access the installed firebase tool
      
      - name: Firebase deploy
        run: |
          firebase deploy
