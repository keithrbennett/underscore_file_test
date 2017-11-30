# UnderscoreFileTest

This illustrates what I believe to be a bug in Ruby 2.4.1.

```
When Ruby version == 2.4.1
  and
current directory is the project root of this project
  and
the gem is built and installed
  and
the executable is run from the gem without preceding it with 'ruby'
(i.e.

Then
  __FILE__ => $PROJECT_ROOT/exe/underscore_file_test
instead of pointing to a directory in the GEM_PATH, something like:
  __FILE__ => /Users/kbennett/.rvm/gems/ruby-2.4.1/bin/underscore_file_test
```

This was tested on the following rubies that did not exhibit the problem:

* 2.0.0-p648
* 2.3.1
* 2.4.0
* jruby-9.1.7.0

## Steps to Reproduce:

* Download or git clone this project tree.
* Change directory to the project root.
* Run: `clear; gem build *gemspec && gem install *gem && underscore_file_test`
* Note the directory component of the output.

If you cd somewhere else, the output will be correct,
i.e. will be located in a GEM_PATH directory.

If you run the command from the project root using a different Ruby,
it may work. I have not tested this on versions _later than_ 2.4.1.
