# Coding Standards

### Q: Does the KBase project using any type of coding standards? Do you use a linter?

We aim to follow [pep8](https://www.python.org/dev/peps/pep-0008/#programming-recommendations), but we have some exceptions,
such as a line length of 100 characters. We don't have a linter. But you can use Flake80 on your code. 

### Q: What python best practices do you recommend?

[Python Best Practices](https://gist.github.com/sloria/7001839)
[An opionated guide to python](http://docs.python-guide.org/en/latest/writing/structure/#object-oriented-programming)
[Raymond Hettinger Videos](http://pyvideo.org/speaker/raymond-hettinger.html)
[Python Gotchas](https://www.toptal.com/python/top-10-mistakes-that-python-programmers-make)

### Q: Which python should I use?

KBase currently uses 2.7.14, but write code compatible with 3, namely wrap your print functions in parenthesis. A guide to writing future proof code is available at
[python-future.org](http://python-future.org/compatible_idioms.html)

Q: Single Quotes or Double Quotes?’
Use single or double quotes consistently throughout your app, pick one and don't switch between the two.

Q: Underscores for protected methods and double underscores for private methods?
YES


