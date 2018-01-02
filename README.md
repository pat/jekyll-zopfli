# Jekyll::Zopfli

Generate gzipped assets and files for your Jekyll site at build time using [Zopfli](https://github.com/google/zopfli) compression.

[![Build Status](https://travis-ci.org/philnash/jekyll-zopfli.svg?branch=master)](https://travis-ci.org/philnash/jekyll-zopfli)

Performance in web applications is important. You know that, which is why you have created a static site using Jekyll. But you want a bit more performance. You're serving your assets and files gzipped, but you're making your webserver do it?

Why not just generate those gzip files at build time? And with Google's Zopfli algorithm, which generates files that are 3-8% smaller than Zlib's maximum compression?

`Jekyll::Zopfli` does just that. Add the gem to your Jekyll application and when you build your site it will generate gzip files for all text based files (HTML, CSS, JavaScript, etc).

### Warning

Zopfli is a much slower algorithm than Zlib, so this will likely significantly slow down your site build. If you still want to generate gzip files at build time with a faster build time and Zlib's compression level, check out [`Jekyll::Gzip`](https://github.com/philnash/jekyll-gzip).

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'jekyll-zopfli'
```

And then execute:

```
bundle install
```

## Usage

Once you have the gem installed, run `bundle exec jekyll build`. In your destination directory (`_site` by default) you will find gzipped files.

### Serving pre-compiled gzip files

You will likely need to adjust your web server config to serve these precomputed gzip files. See below for common server configurations:

#### nginx

For nginx, you need to turn on the [`gzip_static` module](http://nginx.org/en/docs/http/ngx_http_gzip_static_module.html). Add the following in the relevant `http`, `server` or `location` block:

```
gzip_static on;
```

The `ngx_http_gzip_static_module` module is not built by default, so you may need to enable using the `--with-http_gzip_static_module` configuration parameter.

#### Other web servers

TODO: instructions for other web servers like Apache, HAProxy, etc.

Do you know how to do this for a different server? Please open a [pull request](https://github.com/philnash/jekyll-zopfli/pulls) or an [issue](https://github.com/philnash/jekyll-zopfli/issues) with the details!

## Development

After checking out the repo, run `bundle install` to install dependencies. Then, run `bundle exec rspec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/philnash/jekyll-zopfli. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Jekyll::Zopfli project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/philnash/jekyll-gzip/blob/master/CODE_OF_CONDUCT.md).
