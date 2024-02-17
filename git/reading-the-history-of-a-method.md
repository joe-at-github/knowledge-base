# Reading the history of a method

When investigating a bug or simply trying to gain more knowledge about the behaviour of a class, you might be interested in understanding how a given method changed over time and what the intended behaviour was at different points in time.

You might have used `git blame` in the past to quickly access the latest commit hash for different lines on that file and for each line of a given method.

Although `git blame` is a nice and easy way of having an overview of which commit changed which line on an entire file, it might not allow you to easily understand how a specific method changed over time.

## What's an alternative?

You can use the `-L` flag with `git log` and pass the method name and path to the relevant file. This will output any commit that ever changed the method, the specific changes to that method, and the commit message.

## Here is how it works

```bash
git log -L :<method_name>:path/to/file

# e.g
git log -L foo:app/lib/bar.rb
```

For this to work, you will also need to add a `.gitattributes` file in the root directory of your repository and add the relevant syntax parsing parameter so that git can adequately parse files using the conventions of the language the files are written in.

Here is an example below, assuming you are working on a project using Ruby.

```bash
# .gitattributes

*.rb    diff=ruby
```