# RESET

If need to reset everything:

```sh
watchman watch-del-all
rm -rf node_modules/
yarn cache clean
yarn install
yarn start --reset-cache
```
