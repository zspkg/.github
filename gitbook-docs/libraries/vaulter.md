---
description: Easy HashiCorp integration
---

# 🔏 Vaulter

## :question:What is Vaulter?

**Vaulter** is a simple _HashiCorp_ vault client wrapper for configuring services.

## :desktop: Usage example

```go
package example

import "github.com/zspkg/vaulter"

const fooVaultSecretKey = "key"

type FooConfig struct {
	Foo string `fig:"foo_key,required"`
	Bar int    `fig:"bar_secret,required"`
}

func GetFooConfig() (FooConfig, error) {
	var (
		cfg         FooConfig
		vaultGetter = vaulter.MustFromEnv()
	)

	if err := vaultGetter.GetVaultSecret(fooVaultSecretKey, &cfg, nil); err != nil {
		// handle error
	}

	return cfg, nil
}
```
