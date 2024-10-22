# Contributing

Thanks for your interest in contributing to rust-landlock!

## Testing vs kernel ABI

For `cargo test` to work, it needs to run only tests that target the Landlock
ABI supported on your currently running kernel. In order to set the tested ABI
use the LANDLOCK_CRATE_TEST_ABI environmental variable like:

```
LANDLOCK_CRATE_TEST_ABI=1 cargo test
```

The above example uses ABI version 1, supported by kernels 5.13 through 5.18.
You should use the ABI matching your actual kernel version.  The test
`current_kernel_abi()` verifies that the ABI you set in the variable matches
your kernel version.

If LANDLOCK_CRATE_TEST_ABI is unset, it defaults to the latest ABI supported by
rust-landlock.

Note that if you are running with older kernels, you will be missing some
tests, which could cause a difference between your local testing and the
github actions CI.  The github actions CI tests against all supported kernel
ABIs.

For more information about Landlock ABIs see https://landlock.io/rust-landlock/landlock/enum.ABI.html
