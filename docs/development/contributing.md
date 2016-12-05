Contributing
============

If you're here, you would like to contribute to this project and you're really welcome!

Bug Reports
-----------

If you find a bug or a documentation issue, please report it or even better: fix it :). If you report it,
please be as precise as possible. Here is a little list of required information:

 - Precise description of the bug
 - Details of your environment (for example: OS, PHP version, installed extensions)
 - Backtrace which might help identifying the bug


Security Issues
---------------

If you discover any security related issues,
please contact us at tobias.nyholm@gmail.com instead of submitting an issue on GitHub.
This allows us to fix the issue and release a security hotfix without publicly disclosing the vulnerability.


Feature Requests
----------------

If you think a feature is missing, please report it or even better: implement it :). If you report it, describe the more
precisely what you would like to see implemented and we will discuss what is the best approach for it. If you can do
some research before submitting it and link the resources to your description, you're awesome! It will allow us to more
easily understood/implement it.


Sending a Pull Request
----------------------

If you're here, you are going to fix a bug or implement a feature and you're the best!
To do it, first fork the repository, clone it and create a new branch with the following commands:

```bash
$ git clone git@github.com:your-name/repo-name.git
$ git checkout -b feature-or-bug-fix-description
```

Then install the dependencies through Composer_:

```bash
$ composer install
```    

Write code and tests. When you are ready, run the tests.
(This is usually [PHPUnit] or [PHPSpec])

```bash
$ composer test
```

When you are ready with the code, tested it and documented it, you can commit and push it with the following commands:

```bash
$ git commit -m "Feature or bug fix description"
$ git push origin feature-or-bug-fix-description
```

Please write your commit messages in the imperative and follow the [guidelines] for clear and concise messages.

Then [create a pull request] on GitHub.

Please make sure that each individual commit in your pull request is meaningful.
If you had to make multiple intermediate commits while developing,
please squash them before submitting with the following commands
(here, we assume you would like to squash 3 commits in a single one):

```bash
$ git rebase -i HEAD~3
```

If your branch conflicts with the master branch, you will need to rebase and re-push it with the following commands:

```bash
$ git remote add upstream git@github.com:orga/repo-name.git
$ git pull --rebase upstream master
$ git push -f origin feature-or-bug-fix-description
```

Coding Standard
---------------

This repository follows the [PSR-2 standard] and so, if you want to contribute,
you must follow these rules.


Semver
------

We are trying to follow [semver]. When you are making BC breaking changes,
please let us know why you think it is important.
In this case, your patch can only be included in the next major version.


Contributor Code of Conduct
---------------------------

This project is released with a [Code of conduct](code-of-conduct.md).
By participating in this project you agree to abide by its terms.

License
-------

All of our packages are licensed under the [MIT license](licence.md).

[PHPUnit]: http://phpunit.de/
[PHPSpec]: http://phpspec.net/
[guidelines]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[create a pull request]: https://help.github.com/articles/creating-a-pull-request/
[semver]: http://semver.org
[PSR-2 standard]: http://www.php-fig.org/psr/psr-2
