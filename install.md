{% method %}
# Installing po-util

Open a terminal and run the following to install po-util.

{% sample lang="bash" name="macOS" %}
On macOS, po-util is installed using [Homebrew](https://brew.sh).

```bash
$ brew tap nrobinson2000/po
$ brew install po
$ po install
```

{% sample lang="bash" name="Linux" %}
On Linux distributions, po-util can be installed by directly running the install script.

```bash
$ bash <( curl -sL https://raw.githubusercontent.com/nrobinson2000/po-util/master/po-util.sh ) install
```

{% common %}
After installing please read the quick-start guide for more information.

{% endmethod %}
