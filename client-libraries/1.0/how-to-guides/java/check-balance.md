# Check the balance of an address in Java

**In this tutorial, you request the balance of IOTA tokens on addresses from a node.**

## IOTA network

In this tutorial, we connect to a node in the [Devnet](root://getting-started/1.1/networks/overview.md).

## Code walkthrough

1. Import the classes

    ```java
    package com.iota;

    import org.iota.jota.IotaAPI;
    import org.iota.jota.error.ArgumentException;
    ```

2. Connect to a node

    ```java
   IOTAAPI api = new IotaAPI.Builder()
            .protocol("https")
            .host("nodes.devnet.iota.org")
            .port(443)
            .build();
    ```

3. Define the address whose balance you want to check

    ```java
    List<String> addresses = new ArrayList<String>();
        addresses.add("LRAZGXSV9FPCOO9OIUYLRLHBUJSBCCDBZC9UBPNMHQAGGI9BODPVIBMVCIKNCFVWWSALEBQMCFINHIVV9D9LYEQXSA");
    ```

    :::info:
    This address must include a [checksum](root://getting-started/1.1/accounts/checksums.md).
    :::

4. Use the `getBalance()` method to ask the IOTA node for the current balance of the address

    ```java
    try {
        long balance = api.getBalance(100, address);
        System.out.printf("Your balance is: %s", balance);
    } catch (ArgumentException e) { 
        // Handle error
        e.printStackTrace(); 
    }
    ```

    In the console, you should see a balance of IOTA tokens:

    ```
    Your balance is 500
    ```

:::success:Congratulations :tada:
You've just checked the balance of an address.
:::

## Run the code

These code samples are hosted on [GitHub](https://github.com/iota-community/java-iota-workshop).

To get started you need [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed on your device.

You also need a Java development environment that uses the [Maven](https://maven.apache.org/download.cgi) build tool.

In the command-line, do the following:

--------------------
### Linux and macOS
```bash
git clone https://github.com/iota-community/java-iota-workshop.git
cd java-iota-workshop
mvn clean install
mvn exec:java -Dexec.mainClass="com.iota.CheckBalance"
```
---
### Windows
```bash
git clone https://github.com/iota-community/java-iota-workshop.git
cd java-iota-workshop
mvn clean install
mvn exec:java -D"exec.mainClass"="com.iota.CheckBalance"
```
--------------------

In the console, you should see a balance of IOTA tokens:

```
Your balance is 500
```

## Next steps

[Listen for live transactions in the Tangle](../java/listen-for-transactions.md).

You can also check the balance of an address, using a utility such as the [Tangle explorer](https://utils.iota.org).