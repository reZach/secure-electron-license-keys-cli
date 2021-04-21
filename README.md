# secure-electron-license-keys-cli

A secure way to generate license keys for your Electron apps.

## Usage

First, you must install the package.
```shell
> npm i secure-electron-license-keys-cli
```

After installing the package, you need to run the cli tool to create the license key you'll package in a given distributable.
```shell
> secure-electron-license-keys-cli # alternately, you can run "selkc"
```

Running the above command will create a `public.key`, `private.key` and `license.data`. Keep the private key **in a safe location**. 

The `public.key` and `license.data` [by default] you will need to put in the _root_ of your Electron app. The [secure-electron-license-keys](https://github.com/reZach/secure-electron-license-keys) package will attempt to decrypt the `license.data` with the `public.key`. If decryption with the public key succeeds, you can act as appropriate within your app (ie. deny access or allow the user to continue).

## Options

There are a number of options you can use to customize your license key generation.

|Arg|Shorthand|Default|Description|
|---|---|---|---|
|--major|-ma|"all"|Represents the major version of your app|
|--minor|-mi|"all"|Represents the minor version of your app|
|--patch|-p|"all"|Represents the patch version of your app|
|--user|-u|""|Represents a unique value, tied to a user (ie. an email)|
|--expire|-e|""|A value when the license expires (ie. could be a date)|
|--public|-pu|"public.key"|The name of the public key when generated|
|--private|-pr|"private.key"|The name of the private key when generated|
|--license|-l|"license.data"|The name of the license data file when generated|
|--output|-o|process.cwd()|The path where the keys/license data file are generated to|

### Samples
Here are some examples of using some of the options in the command line.

```shell
> secure-electron-license-keys-cli --major "2"
```

```shell
> secure-electron-license-keys-cli --major "2" --expire "2022-06-05"
```

```shell
> secure-electron-license-keys-cli --expire "2022-12-25" --user "uniqueuseremail@account.com"
```

> Note - you can also use the shorthand (ie. `selkc` instead of `secure-electron-license-keys-cli`)