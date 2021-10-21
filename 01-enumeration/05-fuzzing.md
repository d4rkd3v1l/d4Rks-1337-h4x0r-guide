# Fuzzing

> Fuzzing or fuzz testing is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program. The program is then monitored for exceptions such as crashes, failing built-in code assertions, or potential memory leaks.  

## SPIKE

> [SPIKE](https://github.com/guilhermeferreira/spikepp) is a protocol fuzzer creation kit. It provides an API that allows a user to create their own fuzzers for network based protocols using the C++ programming language. The tool defines a number of primitives that it makes available to C coders, which allows it to construct fuzzed messages called “SPIKES” that can be sent to a network service …  


### Related

[An Introduction to Fuzzing: Using fuzzers (SPIKE) to find vulnerabilities](https://resources.infosecinstitute.com/intro-to-fuzzing/)

### Basic uage

test.spk
```
s_readline(); 
s_string_variable("COMMAND");
```

```bash
generic_send_tcp <ip> <port> test.spk 0 0
```
