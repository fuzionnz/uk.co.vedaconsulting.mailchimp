# PHPUnit Integration Tests

These tests can be run with drush. They rely on the actual CiviCRM installation
and a live Mailchimp account, so it's important that this is a safe thing to do!

## Requirements and how to run.

Your CiviCRM must have a valid API key set up and that Mailchimp account must
have at least one list.

You need [phpunit](https://phpunit.de/manual/current/en/installation.html) to
run these tests. Example usage

You **must** start from the docroot of your site. e.g.

    $ cd /var/www/my.civicrm.website/

Run the simplest connection test. A dot means a successful test pass.

    $ phpunit.phar --filter testConnection civicrm_extensions_dir/uk.co.vedaconsulting.mailchimp/tests/integration/
    PHPUnit 5.2.12 by Sebastian Bergmann and contributors.

    .                                                                   1 / 1 (100%)

    Time: 478 ms, Memory: 38.75Mb

    OK (1 test, 3 assertions)

Run all integration tests:

    $ phpunit.phar civicrm_extensions_dir/uk.co.vedaconsulting.mailchimp/tests/integration/

## Troubleshooting

**All the tests failed! 300 errors?!**

May indicate that your CiviCRM DB does not have the Mailchimp extension
installed, especially if you see *"Expected to find the Custom Field with name
Mailchimp_Group"* and similar exceptions. Make sure the extension is installed
(which will add some custom fields for Group entities), that you've configured
the API key in Mailchimp settings, that a Group is configured to connect to a
list, etc.
