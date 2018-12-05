# travis-ansible-testing

This role is purely for integrating with Ansible roles in order to conduct
Travis CI tests using Docker containers.

## Updating .travis.yml

Run the following to update the Ansible role name in `.travis.yml`:

```bash
./setup_travis_tests.sh
...
Enter the Ansible role name: test-role
```

## Using In Ansible Roles

In regards to using these tests within a new or existing Ansible role you may
do the following in order to integrate these tests.

```bash
export TRAVIS_TEST_VER="v1.6.1"
wget https://github.com/mrlesmithjr/travis-ansible-testing/archive/$TRAVIS_TEST_VER.tar.gz
tar zxvf $TRAVIS_TEST_VER.tar.gz --strip 1 --exclude="README.md"
./setup_travis_tests.sh
```

> NOTE: You must also setup Travis integration for the repo you would like to
> integrate with.

## ansible-lint

We have implemented [`ansible-lint`](https://github.com/willthames/ansible-lint)
as part of these tests.

> NOTE: ansible-lint checks playbooks for practices and behaviour that could potentially be improved

If `ansible-lint` detects something the testing will fail. So you need to ensure
that your code aligns to `ansible-lint` practices. There are a few ways that you
can resolve these issues if the code being detected is determined to be accurate.
Use the [following](https://github.com/willthames/ansible-lint#false-positives) as
how to resolve these alerts.

## yamllint

We have implemented [`yamllint`](https://github.com/adrienverge/yamllint) to
ensure that all `YAML` files are valid.

> NOTE: yamllint does not only check for syntax validity, but for weirdnesses
> like key repetition and cosmetic problems such as lines length, trailing spaces,
> indentation, etc.

## License

MIT

## Author Information

Larry Smith Jr.

- [EverythingShouldBeVirtual](http://everythingshouldbevirtual.com)
- [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
- <mailto:mrlesmithjr@gmail.com>
