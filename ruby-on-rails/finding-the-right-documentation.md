# Finding the right documentation

When working on a Ruby on Rails project, you might need to research how a given Rails-provided method works. 
In this scenario, you might want to access the Ruby on Rails documentation.

You might also be interested in learning in broader terms about how to do things with RubyOnRails, in which case you will be after the RubyOnRails guides.

In those scenarios, you will likely use a search engine to look for either the documents, the guides, or the name of the feature you want documentation for.

While this is a good general approach, you might end up finding the latest version of those documents and documentation. The interface might have changed slightly between the RubyOnRails version your project is using and the one you just found.

## What's an alternative?

Thankfully, the Ruby on Rails documentation and guides have a predictable naming convention for their URLs. You can make use of that by writing a script that allows you to detect which version of Ruby on Rails your project is using and open either the documents or the guides, depending on what you are after.

## How?

Declare the following in a file storing custom bash scripts:

```bash
function railsguides {
  VERSION=$(bundle exec rails -v | awk '{print $2}')
  open https://guides.rubyonrails.org/v$VERSION/
}

function railsdocs {
  VERSION=$(bundle exec rails -v | awk '{print $2}')
  open https://api.rubyonrails.org/v$VERSION/
}
```

You can then simply type `railsguides` or `railsdocs` from the terminal session, from the repository you are working from to access the correct resource.