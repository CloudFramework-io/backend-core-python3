# Deploying new version of cloudframework
To add new version of cloudframework: https://pypi.org/project/cloudframework

1 - Verify you have the credentials of cloudframework
`~/.pypirc`
```
[distutils] 
index-servers=pypi

[pypi]
repository: https://upload.pypi.org/legacy/ 
username: <your username>
password: <your password>

[testpypi]
repository: https://test.pypi.org/legacy/
username: <your username>
password: <your password>
```
2 - Download Framework repository 
```
git clone https://github.com/CloudFramework-io/appengine-python-core-3.9.git
```
3 - Make the changes under `appengine-python-core-3.9.git/cloudframework`

4 - Modify `setup.py` and add a change version.
```
..
..

setuptools.setup(
    name="cloudframework",
    version="1.0.1",
    ..
```
5 - Commit and push your changes
6 - Deploy to pypi.org
```
python3 setup.py sdist bdist_wheel
python -m twine upload dist/*
```
The first line runs the setup.py script and creates a wheel distribution package that pip will use to install your library.
The second line uploads your library to the pip server.

## Thank you to ..
* [@pietrassyk](https://medium.com/@pietrassyk) for his manual about [building pip libraries](https://medium.com/@pietrassyk/building-a-custom-pip-library-for-python-fe618034d54a)
