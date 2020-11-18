# Troubleshooting

**You may find some of these issues while creating an IOTA network with Compass.**

:::danger:
This software is now **deprecated**. See [Set up a private Tangle as a Hornet plugin
](root://hornet/1.1/tutorials/set-up-a-private-tangle-hornet.md) for an up-to-date private Tangle.
:::


## Got permission denied while trying to connect to the Docker daemon socket

You may see this error when you run any command that includes `bazel run //docker`.

1. Add your current user to the docker group. Change the `$USER` variable to your username.

    ```bash
    sudo usermod -a -G docker $USER
    ```

2. Restart your Linux server and try again

## Malformed snapshot state file

You may see this error when you run the IOTA node.

In the `snapshot.txt` file, remove any line break characters.

## NumberFormatException

You may see this error when you run the IOTA node.

In the `snapshot.txt` file, remove any spaces after the semicolon.

## IllegalArgumentException

You may see this error when you run the IOTA node.

In the `snapshot.txt` file, remove any spaces before the semicolon.
