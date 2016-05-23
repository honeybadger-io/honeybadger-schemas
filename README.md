# honeybadger-schemas

JSON schemas for Honeybadger API resources.

## Deployment

To deploy you must install Python and [aws-cli](https://github.com/aws/aws-cli):

```sh
brew install python && pip install awscli
```

You also need to configure aws-cli. Grab the security credentials for
honeybadger-schemas from the shared keychain on Dropbox:

```sh
aws configure set preview.cloudfront true

# You can use any of the configuration methods mentioned in the aws-cli README.
export AWS_ACCESS_KEY_ID=[Key]
export AWS_SECRET_ACCESS_KEY=[Secret Key]
```

Then to deploy:

```sh
# Test deployment. (optional)
aws s3 sync public s3://honeybadger-schemas --acl public-read --dryrun

# Deploy files.
aws s3 sync public s3://honeybadger-schemas --acl public-read

# It will take a while for the cache to invalidate.
open http://honeybadger-schemas.s3-website-us-east-1.amazonaws.com
```

## Serving locally via Pow

```sh
gem install powder
powder link schemas
powder open
```

## Testing in the Rails app

These schemas are currently copied manually into our Rails repo at
*spec/fixtures/schemas/*. Eventually we may gem-ify this repo to avoid the
duplication.

## Tests

TODO

## Contributing

If you're adding a new feature, please [submit an
issue](https://bitbucket.org/honeybadgerio/honeybadger-schemas/issues/new) as a
preliminary step; that way you can be (moderately) sure that your pull request
will be accepted.

### To contribute your code:

1. Fork it.
2. Create a topic branch `git checkout -b my_branch`
3. Commit your changes `git commit -am "Boom"`
3. Push to your branch `git push origin my_branch`
4. Send a [pull request](https://bitbucket.org/honeybadgerio/honeybadger-schemas/pull-requests/)
