===============================
srwpy
===============================

.. image:: https://img.shields.io/travis/srwpy/srwpy.svg
        :target: https://travis-ci.org/srwpy/srwpy

.. image:: https://ci.appveyor.com/api/projects/status/8e0gwxyn27ookg8s?svg=true
        :target: https://ci.appveyor.com/project/mrakitin/srwpy

.. image:: https://img.shields.io/pypi/v/srwpy.svg
        :target: https://pypi.python.org/pypi/srwpy


Synchrotron Radiation Workshop

Based on:

* https://github.com/ochubar/SRW for the source code
* https://github.com/NSLS-II/scientific-python-cookiecutter for the structure and features


Licensing and documentation:

* Free software: 3-clause BSD license

Compilation in Windows
----------------------
* install OASYS
* install Visual Studio 2019 with c++ tools
* Start the Visual Studio Command Prompt (check then "where msbuild") (or add VS to your path, typically "C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\VC\\Auxiliary\\Build\\vcvarsall.bat"  amd64 -vcvars_ver=14.16)
* Set the wanted python: 
   - extend PATH with python (set PATH=c:\\Python37\;c:\\Python37\\Lib;c:\\Python37\\libs;%PATH%); or
   - Activate miniconda "c:\\miniconda3\\Scripts\\activate"
* python setup.py bdist_wheel
* python -m twine upload dist\*


Notes on windows compilation
----------------------------

* The libfftw* libraries [*.lib at the main level and core/vc/*.lib] are pre-compiled (not done with setup.py)
* the main compilation is in core/vs/make.bat that compiles a VS project SRWLIB.vcxproj (using msbuild). This is called by setup.py
* then run python setup.py bdist_wheel with the wanted python (from miniconda https://repo.anaconda.com/miniconda/ or the ones from https://www.python.org/downloads/)
* the libfftw*.dll are placed by 'pip install' at the main level of python dir (...\miniconda3\*.dll or ...\Python3.7\*.dll) that must be in %PATH%
* the branch visualstudio2022 contains SRWLIB.vcxproj for Visual Studio 2022
* Windows wheels for python 3.8 and 3.9 are created by @srio using python from python.org and VS 2022. The 3.7 version is created by @lrebuffi usinh VS2019. 
* Wheels directory is https://pypi.org/project/oasys-srwpy/#files

Note that:
----------
* git dir is OASYS1-srwpy: https://github.com/oasys-kit/OASYS1-srwpy
* pip install oasys-srwpy: https://pypi.org/project/oasys-srwpy
* import in python with: "from oasys_srw.srwlib import * " and maybe also "from oasys_srw.uti_plot import * "

