# Swap Cookbook

[![Build Status](https://travis-ci.org/sethvargo-cookbooks/swap.png?branch=master)](https://travis-ci.org/sethvargo-cookbooks/swap) [![Code Climate](https://codeclimate.com/github/sethvargo-cookbooks/swap.png)](https://codeclimate.com/github/sethvargo-cookbooks/swap) [![Dependency Status](https://gemnasium.com/sethvargo-cookbooks/swap.png)](https://gemnasium.com/sethvargo-cookbooks/swap)

This cookbook provides an LWRP for easily creating and managing swap files.

## Requirements

### Platforms

- Debian / Ubuntu derivatives
- RHEL and derivatives
- Fedora
- openSUSE / SUSE Linux Enterprises

### Chef

- Chef 11+

### Cookbooks

- none
## Usage

Add a new swap:

```ruby
swap_file '/mnt/swap' do
  size      1024    # MBs
end
```

Or remove an existing one:

```ruby
swap_file '/mnt/swap' do
  action    :remove
end
```

### LWRP Attributes

Attribute | Description                                 | Example   | Default
--------- | ------------------------------------------- | --------- | -------
path      | The path to put the swap file on the system | /mnt/swap |
size      | The size (in MBs) for the swap file         | 2048      |
persist   | Persist the swapon                          | true      | false

## Installation

If you're using [berkshelf](https://github.com/RiotGames/berkshelf), add `swap` to your `Berksfile`:

```ruby
cookbook 'swap'
```

Otherwise, install the cookbook from the community site:

```
knife cookbook site install swap
```

Have any other cookbooks depend on this cookbook by adding it to the `metadata.rb`:

```ruby
depends 'swap'
```

Now you can use the LWRP in your cookbook!

## ChefSpec matchers

### create_swap_file(path)

Assert that the Chef run creates swap_file.

```ruby
expect(chef_run).to create_swap_file(path).with(
  :size => 1024
)
```

### remove_swap_file(path)

Assert that the Chef run removes swap_file.

```ruby
expect(chef_run).to remove_swap_file(path)
```

## Contributing

1. Fork the project
2. Create a feature branch corresponding to you change
3. Commit and test thoroughly
4. Create a Pull Request on github

  - ensure you add a detailed description of your changes

## License & Authors

- Author:: Seth Vargo (sethvargo@gmail.com)

```text
Copyright 2012-2016, Seth Vargo

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
