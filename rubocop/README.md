# Carbon Five Rubocop Conventions

We like and recommend Rubocop, with the caveat that a handful of its rules can be overly strict out of the box. We've found that development teams benefit from relaxing some of the default settings in order to remove unnecessary friction. This directory contains the configuration we consider standard practice for all of our internal Ruby code bases and a good starting point for starting greenfield client projects.

## Installation

### Making your own copy (recommended!)

The safest way to use the standard Carbon Five Rubocop configuration is to copy all the `.rubocop*.yml` files from this repo into your project. Here is a quick way to do it with `wget`:

```
cd my-rails-app
wget https://raw.githubusercontent.com/carbonfive/c5-conventions/main/rubocop/.rubocop{,-common,-performance,-rails,-rspec}.yml
```

#### Without Rails

The default `.rubocop.yml` assumes you are using Rails, but you can also pick and choose from the individual files that apply to your project. For example, if you aren't using Rails or Rspec, copy the other files that matter to you and construct your own `.rubocop.yml` configuration, like this:

```yaml
require:
  - rubocop-performance

inherit_from:
  - ./.rubocop-common.yml      # copied from c5-conventions
  - ./.rubocop-performance.yml # copied from c5-conventions
```

### Inheriting directly from this repo

Alternatively, if you want your project's configuration to always be exactly in sync with the latest C5 conventions, create a `.rubocop.yml` file in your project:

```yaml
require:
  - rubocop-performance
  - rubocop-rails
  - rubocop-rspec

inherit_from:
  - https://raw.githubusercontent.com/carbonfive/c5-conventions/main/rubocop/.rubocop-common.yml
  - https://raw.githubusercontent.com/carbonfive/c5-conventions/main/rubocop/.rubocop-performance.yml
  - https://raw.githubusercontent.com/carbonfive/c5-conventions/main/rubocop/.rubocop-rails.yml
  - https://raw.githubusercontent.com/carbonfive/c5-conventions/main/rubocop/.rubocop-rspec.yml
```

:warning: If you inherit directly from c5-conventions like this, your Rubocop configuration will be subject to change without notice! We may alter the configuration in ways that cause your project to suddenly be out of compliance.
