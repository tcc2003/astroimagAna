Record the problem and approach in installing scousepy.

1. problem
   ```
   WARNING: The wheel package is not available.
   /bin/python: No module named pip
   Traceback (most recent call last):
       File "/usr/lib/python3.9/site-packages/setuptools/installer.py", line 75, in fetch_build_egg
         subprocess.check_call(cmd)
       File "/usr/lib64/python3.9/subprocess.py", line 373, in check_call
         raise CalledProcessError(retcode, cmd)
   subprocess.CalledProcessError: Command '['/bin/python', '-m', 'pip', '--disable-pip-version-check', 'wheel', '--no-deps', '-w', '/tmp/tmpnd24_7ps',
   '--quiet', 'extension_helpers']' returned non-zero exit status 1.

   The above exception was the direct cause of the following exception:

   Traceback (most recent call last):
       File "/home/tcc/software/scousepy/setup.py", line 12, in <module>
         setup()
       File "/usr/lib/python3.9/site-packages/setuptools/__init__.py", line 152, in setup
         _install_setup_requires(attrs)
       File "/usr/lib/python3.9/site-packages/setuptools/__init__.py", line 147, in _install_setup_requires
         dist.fetch_build_eggs(dist.setup_requires)
       File "/usr/lib/python3.9/site-packages/setuptools/dist.py", line 721, in fetch_build_eggs
         resolved_dists = pkg_resources.working_set.resolve(
       File "/usr/lib/python3.9/site-packages/pkg_resources/__init__.py", line 766, in resolve
         dist = best[req.key] = env.best_match(
       File "/usr/lib/python3.9/site-packages/pkg_resources/__init__.py", line 1051, in best_match
         return self.obtain(req, installer)
       File "/usr/lib/python3.9/site-packages/pkg_resources/__init__.py", line 1063, in obtain
         return installer(requirement)
       File "/usr/lib/python3.9/site-packages/setuptools/dist.py", line 780, in fetch_build_egg
         return fetch_build_egg(self, req)
       File "/usr/lib/python3.9/site-packages/setuptools/installer.py", line 77, in fetch_build_egg
         raise DistutilsError(str(e)) from e
     distutils.errors.DistutilsError: Command '['/bin/python', '-m', 'pip', '--disable-pip-version-check', 'wheel', '--no-deps', '-w', '/tmp/tmpnd24_7ps',
      '--quiet', 'extension_helpers']' returned non-zero exit status 1.
  ```

  **approach**
  The error is due to the absence of the pip and wheel modules in my system. Run:  

  ```
     curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py   
     python get-pip.py   
     pip install wheel   
  ```

2. problem
   ```
   /home/tcc/software/scousepy/.eggs/setuptools_scm-8.1.0-py3.9.egg/setuptools_scm/_integration/setuptools.py:31: RuntimeWarning: 
   ERROR: setuptools==53.0.0 is used in combination with setuptools_scm>=8.x

   Your build configuration is incomplete and previously worked by accident!
   setuptools_scm requires setuptools>=61

   Suggested workaround if applicable:
      - migrating from the deprecated setup_requires mechanism to pep517/518
        and using a pyproject.toml to declare build dependencies
        which are reliably pre-installed before running the build tools
  ```   

  **approach**
  ```
  conda install setuptools>=61  
  conda install setuptools_scm>=8.x # Make sure it is installed.
  python -c "import setuptools; print(setuptools.__version__)" #Check the version
  ```   
  It seems that I cannot install setuptools_scm>=8.x in python 3.7 environment. Use the python 3.9 environment is better.   
  
  It may showed the version of setuptools still be the same as the older one. The issue arises because I am using different Python interpreters    
  or pip installation tools in different environments, leading to version inconsistencies. Run the following command to check :
  ```
  which python
  which pip
  ```
  If the paths are different, run ```vim ~/.bashrc``` and modify ```export PATH=/bin:$PATH``` to ```export PATH="/home/tcc/software/anaconda3/envs/test/bin:$PATH"```.

3. problem
   After running ```python setup.py install```, I get the error message
   ```
   /home/tcc/software/anaconda3/envs/test/lib/python3.9/site-packages/setuptools/__init__.py:85: _DeprecatedInstaller: setuptools.installer and fetch_build_eggs are deprecated.
   !!

        ********************************************************************************
        Requirements should be satisfied by a PEP 517 installer.
        If you are using pip, you can try `pip install --use-pep517`.
        ********************************************************************************
   !!
      dist.fetch_build_eggs(dist.setup_requires)
   running install
   /home/tcc/software/anaconda3/envs/test/lib/python3.9/site-packages/setuptools/_distutils/cmd.py:66: SetuptoolsDeprecationWarning: setup.py install is deprecated.
   !!

        ********************************************************************************
        Please avoid running ``setup.py`` directly.
        Instead, use pypa/build, pypa/installer or other
        standards-based tools.

        See https://blog.ganssle.io/articles/2021/10/setup-py-deprecated.html for details.
        ********************************************************************************

   !!
     self.initialize_options()
   /home/tcc/software/anaconda3/envs/test/lib/python3.9/site-packages/setuptools/_distutils/cmd.py:66: EasyInstallDeprecationWarning: easy_install command is deprecated.
   !!

        ********************************************************************************
        Please avoid running ``setup.py`` and ``easy_install``.
        Instead, use pypa/build, pypa/installer or other
        standards-based tools.

        See https://github.com/pypa/setuptools/issues/917 for details.
        ********************************************************************************

   !!
    self.initialize_options()
   running bdist_egg
   running egg_info
   error: Cannot update time stamp of directory 'scousepy.egg-info'
   ```
   **approach**
   



