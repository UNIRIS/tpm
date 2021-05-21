# TPM Core
## Depends on [TPM2-TSS](https://github.com/tpm2-software/tpm2-tss)

## Compiling the library
```console
$ gcc uniris-tpm.c -o uniris-tpm -ltss2-esys -c
```

## Testing with a driver
```console
$ gcc driver.c -o driver uniris-tpm -ltss2-esys
$ sudo ./driver
```

## One step driver compilation
```console
$ gcc driver.c -o driver uniris-tpm.c -ltss2-esys
$ sudo ./driver
```

## Compiling TPM-core for Elixir support
Make sure that Erlang and Elixir are already installed on the system.
```console
$ gcc support.c -o support stdio_helpers.c uniris-tpm.c -ltss2-esys
```

## Required commands at the start of a new session
```console
$ sudo iex tpm-lib.ex
$ TPMPort.start_link
$ TPMPort.initialize_tpm(KEY_INDEX)
```

## Library Functions for Elixir support
```console
$ TPMPort.get_public_key(KEY_INDEX)
$ sign_ecdsa(KEY_INDEX, HASH_SHA256)
$ TPMPort.get_key_index()
$ TPMPort.set_key_index(KEY_INDEX)
```
