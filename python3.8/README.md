# Chiselled Python3.8

This directory contains the image recipes of Chiselled Python3.8. These images are smaller in size,
hence less prone to vulnerabilities. Know more about chisel [here](https://github.com/canonical/chisel).

We currently have Chiselled Python3.8 only on focal. See [Dockerfile.20.04](./Dockerfile.20.04).

### Building the image(s)

Build the dockerfile(s) in the usual way:

```sh
$ docker build -t ubuntu/chiselled-python:3.8 -f python3.8/Dockerfile.20.04 python3.8
```

### Run the image(s)

The image has the "python3.8" binary as the entrypoint.

```sh
$ docker run -it ubuntu/chiselled-python:3.8
Python 3.8.10 (default, May 26 2023, 14:05:08)
[GCC 9.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("hello world")
hello world
>>> exit()
```

### Building and running an application on Chiselled Python3.8

Let's assume, you have the following Python3 source code you want to run as an application. Assume the file is called `main.py`.

```py
print("hello world")
```

You may create the following Dockerfile for your application image:

```Dockerfile
FROM ubuntu/chiselled-python:3.8

ADD main.py /

ENTRYPOINT ["python3.8", "/main.py"]
```

Build the image:

```sh
$ docker build -t myapp -f Dockerfile.app .
```

Run your application container:

```sh
$ docker run myapp
hello world
```
