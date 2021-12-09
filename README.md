[![godot-ci export](https://github.com/PanLabGameDev/godot-boilerplate/actions/workflows/godot-ci.yml/badge.svg)](https://github.com/PanLabGameDev/godot-boilerplate/actions/workflows/godot-ci.yml)
[![godot-export](https://github.com/PanLabGameDev/godot-boilerplate/actions/workflows/godot-export.yml/badge.svg)](https://github.com/PanLabGameDev/godot-boilerplate/actions/workflows/godot-export.yml)

# godot-boilerplate

This is a boilerplate repository for any godot v3.4 game

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
- Go to github repository > Settings > Secrets > [New Repository Secret]
- Name it: ANDROID_KEYSTORE
- Set the value to the content of that .asc file (including `-----BEGIN PGP MESSAGE-----...`)
- Create another Secret:
- Name it: ANDROID_KEYSTORE_PASS
- Set the value to the password you have chosen when asked by gpg.
