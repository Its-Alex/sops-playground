# SOPS with Age - Integration Example

This repository demonstrates a simple integration of [SOPS](https://github.com/getsops/sops)
with age for encrypting secrets in Git.

## Requirements

- [mise](https://mise.jdx.dev/)

When [mise](https://mise.jdx.dev/) is installed you must execute:

```shell
$ mise trust && mise install
```

## Getting started

This repository is just an example of how to handle secrets with SOPS in a
repository using [age](https://github.com/FiloSottile/age) to seamlessly
encrypt sensitive content.

### Configuration

[Age](https://github.com/FiloSottile/age) keys can be found in [keys](./keys/)
folder.

[Sops](https://github.com/getsops/sops) configuration can be found in
[.sops.yaml](.sops.yaml).

This repository aim to handle a [.env](.env) file.

### Decrypt

This command will decrypt and replace file with decrypted content:

```sh
$ sops -d -i .env
```

### Encrypt

This command will encrypt and replace file with encrypted content:

```sh
$ sops -e -i .env
```

## Thoughts

Using Sops in day-to-day work is quite straightforward, similar to
[passwordstore](https://www.passwordstore.org/) but with significantly more
capabilities:

- Configuration file that clearly shows what's encrypted with which key
- Can be [synced with a Vault](https://github.com/getsops/sops?tab=readme-ov-file#publishing-to-vault)
- Multiple encryption support
- Partial file encryption
- [Key groups](https://github.com/getsops/sops?tab=readme-ov-file#id24) support
- [Auditing](https://github.com/getsops/sops?tab=readme-ov-file#auditing) support

However, in my particular use case, I often don't need these advanced features. 
I'm mainly looking for a streamlined workflow that allows developers to handle 
passwords transparently without additional complexity.

There are some drawbacks in the user experience, for example
[Support input/output type overrides (configuration/metadata)](https://github.com/getsops/sops/issues/813)

## License

[MIT](LICENSE)