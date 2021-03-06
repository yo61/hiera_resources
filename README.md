# hiera_resources

#### Table of Contents

1. [Overview](#overview)
2. [Module Description - What the module does and why it is useful](#module-description)
3. [Beginning with hiera_resources](#beginning-with-hiera_resources)
4. [Usage - Configuration options and additional functionality](#usage)
5. [Credit](#credit)

## Overview

Allow arbitrary definition of resources (classes and defined types) via hiera content while avoiding the hiera_hash/create_resources pattern.

## Module Description

If applicable, this section should have a brief description of the technology
the module integrates with and what that integration enables. This section
should answer the questions: "What does this module *do*?" and "Why would I use
it?"

If your module has a range of functionality (installation, configuration,
management, etc.) this is the time to mention it.

## Beginning with hiera_resources

hiera_resources() allows you to use arbitrary hiera data to create and manage
classes and defined types. Provide a hash with a top level name followed by
a second level resource type and subsequent levels containing the required
resource parameters and values.

For instance, given the following hiera YAML file:

    ---
    messages1:
      notify:
        title 1:
          message: this is the first message stored in YAML
        title 2:
          message: this is the second message stored in YAML

You may include `hiera_resources('messages1')` in a manifest to create two
notify resources, 'title 1' and 'title 2'.

hiera_resources() does not verify the contents of the hash or referenced
resource type. It does accept a second value as a default value if the lookup
fails, following the same tiered hierarchy as the hiera hash.

## Usage

Ensure that hiera_resources is in your `$modulepath` and that `pluginsync` is
set to true on the master. You may then use hiera_resources() in your
manifests.

## Credits

This version of hiera_resources is based on
[this excellent blog post](http://blog.yo61.com/assigning-resources-to-nodes-with-hiera-in-puppet/)
by Robin Bowes and a subsequent
[refactoring](https://github.com/reliantsecurity/hiera-resources).
