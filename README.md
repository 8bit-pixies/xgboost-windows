xgboost-windows
===============

Useful things for xgboost windows installation

Instructions
------------

These instructions are based on [this post](https://www.ibm.com/developerworks/community/blogs/jfp/entry/Installing_XGBoost_For_Anaconda_on_Windows?lang=en)

### Dependencies

*  cmder or similar tool
*  `MinGW-W64`, provided in this repository
*  Anaconda Python install

1. Clone the repo

This can be done in the normal "cmd" environment within `cmder`

```sh
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost
git submodule init
git submodule update
```

and add the relevant `alias`:

```sh
alias make='mingw32-make'
```

2. Build the stuff

This has to be done in the `bash` environment within `cmder`.

```sh
cd dmlc-core
make -j4
cd ../rabit
make lib/librabit_empty.a -j4
cd ..
cp make/mingw64.mk config.mk
make -j4
```

3. Done!

You can build the python module; just make sure MinGW-W64 has the path variable set when you `import xgboost`.
