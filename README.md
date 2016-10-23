# Internals

[Debian] (currently 64-bit Jessie) virtual machine used to simplify the
development of [PHP] internals.

This will install everything required to compile and test PHP within the
virtual machine and includes [GDB] and [Valgrind] for debugging and
instrumentation. The only requirement is that this repository exists within
the same directory as where your cloned PHP repository exists.

## Requirements

* The [PHP repository] cloned within the same directory as this repository
* [Vagrant version 1.7+](https://www.vagrantup.com)

## Example setup

```bash
$ cd ~/Projects
$ git clone git@github.com:php/php-src.git
$ git clone git@github.com:unfunco/internals.git
$ cd internals
$ vagrant up
```

You can edit the internals code from your host machine as NFS is specified
within the [Vagrantfile], but you will need to `vagrant ssh` into the
virtual machine in order to compile and run tests.

```bash
$ cd internals
$ vagrant ssh
$ cd php-src
$ ./buildconf
$ ./configure
$ make
$ # Run the entire PHP test suite
$ make test
$ # ...or run one or more tests by specifying a directory or filename, e.g.
$ sapi/cli/php run-tests.php -P ext/standard/tests/array
$ # ...and assuming nobody has broken anything, it should end something like:
=====================================================================
Number of tests :  930               918
Tests skipped   :   12 (  1.3%) --------
Tests warned    :    0 (  0.0%) (  0.0%)
Tests failed    :    0 (  0.0%) (  0.0%)
Expected fail   :    0 (  0.0%) (  0.0%)
Tests passed    :  918 ( 98.7%) (100.0%)
---------------------------------------------------------------------
```

If you step in and out of playing with internals with the delays that
I am guilty of, then it's possible that the time on the guest machine can
become out of synchronisation, run `make clean` to fix this issue.

## Todo

* [ ] Add aliases to each compilation and testing

## License

Copyright © 2016 [Daniel Morris](https://github.com/unfunco)  
Licensed under the terms of [The MIT License](LICENSE.md).

[Debian]: https://www.debian.org
[GDB]: https://www.gnu.org/software/gdb/
[PHP]: https://secure.php.net
[PHP repository]: https://github.com/php/php-src
[Vagrantfile]: Vagrantfile
[Valgrind]: http://www.valgrind.org
