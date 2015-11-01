P/Invoke
=======

[![Build status](https://ci.appveyor.com/api/projects/status/idu56hy4jwytxd3x?svg=true)](https://ci.appveyor.com/project/AArnott/pinvoke)
[![Join the chat at https://gitter.im/AArnott/pinvoke](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/AArnott/pinvoke?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A library intended to contain all P/Invoke method signatures for popular operating systems.
Think of it as http://pinvoke.net, but proven to compile and work properly, and often
with sample usage in the form of unit tests.

## Usage

Install the NuGet package(s) for the DLLs you want to P/Invoke into.
For example, if you want to P/Invoke into Win32's BCrypt.dll, install this package:

    Install-Package PInvoke.BCrypt

Then import the following namespaces, as demonstrated below (if using C# 6):

    using PInvoke;
    using static PInvoke.BCrypt; // Supported in C# 6 (VS2015) and later.

This will allow you to conveniently call these methods directly by method name:

    var error = BCryptOpenAlgorithm(AlgorithmIdentifiers.BCRYPT_SHA256_ALGORITHM); // C# 6 syntax
    var error = BCrypt.BCryptOpenAlgorithm(BCrypt.AlgorithmIdentifiers.BCRYPT_SHA256_ALGORITHM); // C# 5 syntax

## Design goals

Provide a slightly higher than lowest level API for P/Invoke signatures.
For example, instead of `IntPtr` parameters and `uint` flags, you'll see `SafeHandle`-derived
types as parameters and flags `enum` types. API documentation will be provided via XML doc comments
for easy reading with Intellisense, along with links to the describing pages on MSDN
or elsewhere as applicable.

This is a portable library so you can use it anywhere.

## Distribution

This library should be available on NuGet for easy consumption by your projects.
You may also copy and paste the P/Invoke signatures you need directly into your projects if desired. 

## Contribution

Please consider [contributing](CONTRIB.md) more P/Invoke method signatures to this project.
Once you contribute, you can immediately consume your additions without waiting for another
public release of the library.
