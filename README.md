# ip6snetc

ip6snetc is a tool for caclulating and listing IPv6 networks.

## Usage

```
ip6snetc <IPv6 network address> [<subnet prefix>]
```

## Examples

### Show information regarding given network / address

```
$ ./ip6snetc 2001:db8::1/32
```
```
 --- IPv6 network / address information:

 Address 2001:db8::1
 Network 2001:db8::/32
  Prefix ffff:ffff:0000:0000:0000:0000:0000:0000
    from 2001:0db8:0000:0000:0000:0000:0000:0000
      to 2001:0db8:ffff:ffff:ffff:ffff:ffff:ffff
    Type IPv6 Address Prefix Reserved for Documentation
     RFC RFC3849
     src false
     dst false
     fwd false
  global false
IPv6 res false
```

### Caclulate and list subnets for given network and subnet prefix

```
$ ./ip6snetc 2001:db8::1/32 33
```
```
 --- IPv6 network / address information:

 Address 2001:db8::1
 Network 2001:db8::/32
  Prefix ffff:ffff:0000:0000:0000:0000:0000:0000
    from 2001:0db8:0000:0000:0000:0000:0000:0000
      to 2001:0db8:ffff:ffff:ffff:ffff:ffff:ffff
    Type IPv6 Address Prefix Reserved for Documentation
     RFC RFC3849
     src false
     dst false
     fwd false
  global false
IPv6 res false

 --- Subnet data:

  Subnet Prefix /33
 Subnets 2

 Network 2001:db8::/33
  Prefix ffff:ffff:8000:0000:0000:0000:0000:0000
    from 2001:0db8:0000:0000:0000:0000:0000:0000
      to 2001:0db8:7fff:ffff:ffff:ffff:ffff:ffff

 Network 2001:db8:8000::/33
  Prefix ffff:ffff:8000:0000:0000:0000:0000:0000
    from 2001:0db8:8000:0000:0000:0000:0000:0000
      to 2001:0db8:ffff:ffff:ffff:ffff:ffff:ffff
```

## Dependencies

ip6snetc is written for luajit and Lua 5.1. It uses lua bitop (http://bitop.luajit.org/) library.

Luajit has BitOp integrated. For standard Lua one needs to install BitOp separately.

### An example of installing Lua BitOp on Gentoo

```
$ sudo emerge -v LuaBitOp
```

## Notes

This script contains a shebang for running with Luajit.

In case you'd like to use standard Lua instead, you'll need to edit the first line of ip6snetc to be:

```
#!/usr/bin/env lua
```

Other option is to call the script directly with Lua. Example:

```
$ lua ip6snetc 2001:db8::1/32
```

