[![godot-export](https://github.com/PanLabGameDev/godot-boilerplate/actions/workflows/godot-export.yml/badge.svg)](https://github.com/PanLabGameDev/godot-boilerplate/actions/workflows/godot-export.yml)

# godot-boilerplate

This is a boilerplate repository for any godot v3.4 game

# Add add repository as upstream

```
# add upstream
git remote add upstream git@github.com:PanLabGameDev/godot-boilerplate.git
# verify
git remote -vv
# merge latest changes
git merge upstream main
```

# Android / APK Export

- Create your own keystore:

```bash
echo y | keytool -genkeypair -keyalg RSA -validity 20000 -dname "cn=Godot, ou=GameDev, o=PanLab, c=AT" -alias godot -keypass godotpass -storepass godotpass -keystore android.keystore
```

- make sure to set your alias and your key-/storepass accordingly in the godot `export_presets.cfg`
- encrypt it using gpg

```bash
gpg -c --armor android.keystore
```

- open the file `android.keystore.asc` in your text editor.
- Go to your github repository > Settings > Secrets: **New Repository Secret**
- Name it: **ANDROID_KEYSTORE**
- Set the value to the content of that .asc file (including `-----BEGIN PGP MESSAGE-----...`)
- Create another secret and name it: **ANDROID_KEYSTORE_PASS**
- Set the value to the password you have chosen when asked by gpg.

# itch.io Export

- Create an account on itch.io:
- Create a new project: https://itch.io/game/new
- Give it a proper name - you can leave the rest empty and update later
- Go to your settings > Api Keys: https://itch.io/user/settings/api-keys
- Click **Generate new API key** and copy the key.
- got to github repository > Settings > Secrets: **New Repository Secret**
- Name it: **ITCHIO_API_KEY**
- Set the API key as content.
- Create another secret and name: **ITCHIO_USER**
- Set your username as content.
- Create another secret and name: **ITCHIO_GAME**
- Set the name of your game as content.
