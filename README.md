# rbvirtualenv

Ruby Virtual Environments Done Right

## Design Goals

1. One step install
2. No hacks
3. Least surprise

## UI Notes

```bash
$ brew install rbvirtualenv
$ apt-get install rbvirtualenv

$ cd myproject
$ rbvirtualenv 1.9.3-p327 .rbv
$ rbv 1.9.3
$ rbv list-rubies
$ rbv add-ruby /path/to/ruby foobar
$ rbv foobar

$ ls .rbv
bin gems

$ cat .rbv/bin/ruby
#!/usr/bin/env bash

SCRIPT_DIR=$(dirname $0)
[ $SCRIPT_DIR == . ] && SCRIPT_DIR=$(pwd)

export GEM_HOME=$SCRIPT_DIR/../gems

if [ $GLOBAL_SITE_PACKAGES = '1' ]; then
  export GEM_PATH=$SCRIPT_DIR/../gems:$GEM_PATH
else
  export GEM_PATH=$SCRIPT_DIR/../gems
fi

exec /path/to/ruby "$@"

$ cd myproject
$ source .rbv/bin/activate

... work work work

$ deactivate
```
