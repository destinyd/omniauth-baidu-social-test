# OmniAuth Baidu OAuth2

Baidu OAuth2 Strategy for OmniAuth 1.0.

Read Baidu OAuth2 docs for more details: http://developer.baidu.com/wiki/index.php?title=docs/social

## Installing

Add to your `Gemfile`:

```ruby
gem 'omniauth-baidu'
```

Then `bundle install`.

Or install it yourself as:

    $ gem install omniauth-baidu

## Usage

`OmniAuth::Strategies::Baidu` is simply a Rack middleware. Read the OmniAuth 1.0 docs for detailed instructions: https://github.com/intridea/omniauth.

Here's a quick example, adding the middleware to a Rails app in `config/initializers/omniauth.rb`:

```ruby
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :baidu, ENV['BAIDU_SOCIAL_KEY'], ENV['BAIDU_SOCIAL_SECRET']
end
```

## Authentication Hash

Here's an example *Authentication Hash* available in `request.env['omniauth.auth']`:

```ruby
{
  :provider => 'baidu',
  :uid => '1234567890',
  :info => {
    :social_uid => '1234567890',
    :name => 'destinyd',
    :media_uid => '0987654321',
    :media_type => 'sinaweibo',
    :is_verified     => raw_info['is_verified']
  },
  :credentials => {
    :token => '2.00JjgzmBd7F...', # OAuth 2.0 access_token, which you may wish to store
    :expires_at => 1331780640, # when the access token expires (if it expires)
    :expires => true # if you request `offline_access` this will be false
  },
  :extra => {
    :raw_info => {
      ... # data from /social/api/2.0/user/info.json, check by yourself
    }
  }
}
```
*PS.* Built and tested on MRI Ruby 1.9.3

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

Copyright (c) 2012 by Bin He

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
