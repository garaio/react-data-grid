## Setup für lokale Entwicklung

- Repo <https://github.com/garaio/react-data-grid> in den lokalen Entwicklungsordner clonen
- im react-data-grid Ordner folgende Befehle absetzen
  - ```npm run build```
  - ```npm run prepublishOnly```
  - ```npm run postbuild```
  - ```yarn link```
  - ```npm link ../rem2/node_modules/react``` (WICHTIG: damit sorgen wir dafür, dass react-data-grid dieselbe react-Version benutzt wie rem2. Macht man das nicht, gibt's ganz komische Javascript-Fehler. Siehe auch <https://reactjs.org/warnings/invalid-hook-call-warning.html>)
- im rem2 Ordner folgenden Befehl absetzen
  - ```yarn link react-data-grid```
  - ```yarn install --force```

Wenn am react-data-grid Änderungen vorgenommen wurden, muss im entsprechenden Ordner ```yarn run build```ausgeführt werden. Mit laufendem webpack-dev-server löst das automatisch einen reload im Browser aus und die Änderungen sind aktiv.

Wenn man den Entwicklungsmodus verlassen will, muss ```yarn unlink react-data-grid``` im rem2 Ordner ausgeführt werden, damit wieder das node module von github verlinkt wird.

## Fixes oder Erweiterungen

Wenn ein von uns erstellter Bugfix oder eine Erweiterung getestet und für gut befunden wurde, muss der topic branch in garaio/stable gemerged werden. Zudem soll - wenn sinnvoll - ein Pull Request erstellt werden, damit die Änderungen in react-data-grid übernommen werden können.

## Neue Version releasen

- Neue Version im package.json eintragen
- Im react-data-grid Ordner den Release publishen: ```npm publish --tag canary --access public```
- Den neuen Release in rem2 einbinden: ```yarn add @garaio/react-data-grid@<version>```
