# SETUP

Usually distributed as npm package, except besides usual JS also includes native code per platform.

```bash
yarn global add create-react-native-module
create-react-native-module MyLibrary
```

Navigate to module folder and:

```bash
yarn install
```

Go to main react app folder and:
1. add module as dependency in `package.json`
2. run `yarn install` to bring it along from local npm repo
