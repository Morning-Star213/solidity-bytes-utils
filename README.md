## _Version Notes_:

* Version `v0.9.0` has a new feature: a new "equal_nonAligned" method that allows for comparing two bytes arrays that are not aligned to 32 bytes.
This is useful for comparing bytes arrays that were created with assembly/Yul or other, non-Solidity compilers that don't pad bytes arrays to 32 bytes.

* Starting from version `v0.8.0` the versioning will change to follow compatible Solidity's compiler versions.
This means that now the library will only compile on Solidity versions `>=0.8.0` so, if you need `<0.8.0` support for your project just use `v0.1.2` of the library with:

```
$ truffle install bytes@0.8.0
```
or
```
$ npm install solidity-bytes-utils@0.8.0
```

* Version `v0.1.2` has a major bug fix.

* Version `v0.1.1` has a critical bug fix.

* Version `v0.9.0` now compiles with Solidity compilers `0.5.x` and `0.6.x`.

* Since version `v0.0.7` the library will only compile on Solidity versions `>0.4.22` so, if you need `v0.4.x` support for your project just use `v0.0.6` of the library with:

```
$ truffle install bytes@0.0.6
```
or
```
$ npm install solidity-bytes-utils@0.0.6
```

## Usage

You can use the library here present by direct download and importing with:
```
import "BytesLib.sol";
```

or, if you have installed it from EPM (see below), with Truffle's specific paths:
```
import "bytes/BytesLib.sol";
```

Usage examples and API are more thoroughly explained below.

Also there's an extra library in there called `AssertBytes` (inside the same named file) which is compatible with Truffle's Solidity testing library `Assert.sol` event firing and so lets you now test bytes equalities/inequalities in your Solidity tests by just importing it in your `.sol` test files:
```
import "bytes/AssertBytes.sol";
```

and use the library `AssertBytes` much like they use `Assert` in Truffle's [example](http://truffleframework.com/docs/getting_started/solidity-tests).

## EthPM

This library is published in EPM under the alias `bytes`

**Installing it with Truffle**

```
$ truffle install bytes
```

## NPM

This library is published in NPM under the alias `solidity-bytes-utils`

**Installing it with NPM**

```
$ npm install solidity-bytes-utils
```

**Importing it in your Solidity contract**

```
import "solidity-bytes-utils/contracts/BytesLib.sol";
```

## Contributing

Contributions are more than welcome in any way shape or form! 😄

TODOs:
* Two storage bytes arrays concatenation
* Slicing directly from storage
* Implement inline assembly functions for better readability

### Testing

This project uses Truffle for tests. Truffle's version of `solc` needs to be at least 0.4.19 for the contracts to compile. If you encounter compilation errors, try:

    $ cd /usr/local/lib/node_modules/truffle
    $ npm install solc@latest

To run the tests, start a `testrpc` instance, then run `truffle test`.

## API

* `function concat(bytes memory _preBytes, bytes memory _postBytes) internal pure returns (bytes)`

Concatenates two `bytes` arrays in memory and returns the concatenation result as another `bytes` array in memory.


* `function concatStorage(bytes storage _preBytes, bytes memory _postBytes) internal pure`

Concatenates a `bytes` array present in memory directly into the given storage location addressed by the `_preBytes` storage pointer.


* `function slice(bytes _bytes, uint _start, uint _length) internal  pure returns (bytes)`

Takes a slice from a `bytes` array in memory of given `length` starting from `_start`th byte counting from the left-most one (0-based).


* `function toAddress(bytes _bytes, uint _start) internal  pure returns (address)`

Takes a 20-byte-long sequence present in a `bytes` array in memory and returns that as an address (also checks for sufficient length).


* `function toUint(bytes _bytes, uint _start) internal  pure returns (uint256)`

Takes a 32-byte-long sequence present in a `bytes` array in memory and returns that as an unsigned integer (also checks for sufficient length).


* `function equal(bytes memory _preBytes, bytes memory _postBytes) internal view returns (bool)`

Compares two `bytes` arrays in memory and returns the comparison result as a `bool` variable.


* `function equalStorage(bytes storage _preBytes, bytes memory _postBytes) internal view returns (bool)`

Compares a `bytes` array in storage against another `bytes` array in memory and returns the comparison result as a `bool` variable.
