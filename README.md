# Nullable database fields for the Laravel PHP Framework

Often times, database fields that are not assigned values are defaulted to `null`. This is particularly important when creating records with foreign key constraints.

Laravel (5.1) does not currently support automatically setting nullable database fields as `null` when the value assigned to a given attribute is empty.

# Installation

This trait is installed via [Composer](http://getcomposer.org/). To install, simply add it to your `composer.json` file:

```
{
	"require": {
		"iatstuti/laravel-nullable-fields": "~1.0"
	}
}
```

Then run composer to update your dependencies:

```
$ composer update
```

In order to use this trait, import it in your Eloquent model, then set the protected `$nullable` property as an array of fields you would like to be saved as `null` when empty.

```php
<?php

use Iatstuti\Database\Support\NullableFields;
use Illuminate\Database\Eloquent\Model;

class UserProfile extends Model
{
	use NullableFields;
	
	protected $nullable = [
		'facebook_profile',
		'twitter_profile',
		'linkedin_profile',
	];
	
}
```

Now, any time you are saving a `UserProfile` profile instance, any empty attributes that are set in the `$nullable` property will be saved as `null`.

```php
<?php

$profile = new UserProfile::find(1);
$profile->facebook_profile = ' '; // Empty
$profile->twitter_profile  = 'michaeldyrynda';
$profile->linkedin_profile = '';  // Empty
$profile->save();
```

# More information

[https://iatstuti.net/blog/working-with-nullable-fields-in-eloquent-models](Working with nullable fields in Eloquent models) - first iteration

# Support

If you are having general issues with this package, feel free to contact me on [Twitter](https://twitter.com/michaeldyrynda).

If you believe you have found an issue, please report it using the [GitHub issue tracker](https://github.com/deringer/laravel-nullable-fields/issues), or better yet, for the repository and submit a pull request.

If you're using this package, I'd love to hear your thoughts. Thanks!