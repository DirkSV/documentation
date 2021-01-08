# Ternary 

**All messages in the Tangle are made up of characters called trytes. This topic explains what ternary is, why IOTA uses it, and how data is converted to trytes.**

:::info:
The Ternary numerical system will be repurposed in the future in the coming IOTA updates.
:::

IOTA uses the ternary numeral system to represent data because, compared to binary, ternary computing is considered to be more efficient as it can represent data in three states rather then just two. See [Why does IOTA use a ternary number system](https://iota.stackexchange.com/questions/8/why-does-iota-use-a-ternary-number-system) on StackExchange for more details.

In IOTA, data is represented in balanced ternary, which consists of 1, 0, or -1. These values are called trits, and three of them are equal to one tryte, which can have 27 (3<sup>3</sup>) possible values.

## Tryte encoding

To make trytes easier to read, they are represented as one of 27 possible tryte-encoded characters, which consist of the number 9 and the uppercase letters A-Z.

|**Tryte-encoded character**| **Trits**| **Decimal number**|
|:----------------------|:-----|:--------------|
|                                  9|  0,  0,  0 |     0|
|                                  A|  1,  0,  0 |     1|
|                                  B| -1,  1,  0 |     2|
|                                  C|  0,  1,  0 |     3|
|                                  D|  1,  1,  0 |     4|
|                                  E| -1, -1,  1 |     5|
|                                  F|  0, -1,  1 |     6|
|                                  G|  1, -1,  1 |     7|
|                                  H| -1,  0,  1 |     8|
|                                  I|  0,  0,  1 |     9|
|                                  J|  1,  0,  1 |    10|
|                                  K| -1,  1,  1 |    11|
|                                  L|  0,  1,  1 |    12|
|                                  M|  1,  1,  1 |    13|
|                                  N| -1, -1, -1 |   -13|
|                                  O|  0, -1, -1 |   -12|
|                                  P|  1, -1, -1 |   -11|
|                                  Q| -1,  0, -1 |   -10|
|                                  R|  0,  0, -1 |    -9|
|                                  S|  1,  0, -1 |    -8|
|                                  T| -1,  1, -1 |    -7|
|                                  U|  0,  1, -1 |    -6|
|                                  V|  1,  1, -1 |    -5|
|                                  W| -1, -1,  0 |    -4|
|                                  X|  0, -1,  0 |    -3|
|                                  Y|  1, -1,  0 |    -2|
|                                  Z| -1,  0,  0 |    -1|

## How ASCII characters are converted to trytes

In the IOTA client libraries, you can convert ASCII characters to and from trytes.

This feature is useful for converting an ASCII message such as `Hello world` to trytes, which you can add to a message.

Each ASCII character is represented as 2 trytes by doing the following:

- Finding the decimal Unicode value of an ASCII character

    For example, the decimal Unicode value of `Z` is 90.

- Using the decimal Unicode value in the following equations:

    ```
    decimal % 27
    (decimal - 9) / 27
    ```

    For example, for `Z`, the result would be

    ```
    90 % 27 = 9
    (90 - 9) / 27 = 3
    ```

- Using the results of the equations as indexes to find the character's tryte value

    For example, the ASCII character `Z` is represented as `IC` in trytes.

    |**Index** |**Trytes**|
    |--|--|
    |0|9|
    |1|A|
    |2|B|
    |**__3__**|**__C__**|
    |4|D|
    |5|E|
    |6|F|
    |7|G|
    |8|H|
    |**__9__**|**__I__**|
    |10|J|
    |11|K|
    |12|L|
    |13|M|
    |14|N|
    |15|O|
    |16|P|
    |17|Q|
    |18|R|
    |19|S|
    |20|T|
    |21|U|
    |22|V|
    |23|W|
    |24|X|
    |25|Y|
    |26|Z|

## Next steps

[Find out about the different types of messages](../first-steps/sending-messages.md) and how you can use them.

