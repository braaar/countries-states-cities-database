# Contributing to Country State City Database

:+1::tada: First off, thanks for taking the time to contribute! :tada::+1:

The following is a set of guidelines for contributing to Contributing to Country State City Database. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

## How Can I Contribute?

### Reporting Data Related Issues
- Raise an issue for data errors.
- Mark those issues with a `bug` label.

### Suggesting Enhancements
- Raise an Issue for suggesting enhancements.
- Mark those issues with a `enhancement` label.

### Fixing Data By Yourself
If you want to fix some data and raise a pull request
- To fix cities records - You need to update `sql/cities.sql` and `sql/world.sql`.
- To fix states/regions records - You need to update `sql/states.sql` and `sql/world.sql`
- To fix countries records - You need to update `sql/countries.sql` and `sql/world.sql`

## `states.sql`
| Column          | Data type       | Explanation    | 
| --------------- | --------------- | -------------- |
| `id`            | `mediumint(8) unsigned NOT NULL AUTO_INCREMENT` | Unique ID |
| `name`          | `varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL` | The name of the state. |
| `country_id`    | `mediumint(8) unsigned NOT NULL` | Unique id of parent country from `countries.sql` **Constraint:** ```FOREIGN KEY (`country_id`) REFERENCES `countries` (`id`)``` |
| `country_code`  | `char(2) COLLATE utf8mb4_unicode_ci NOT NULL`  | [ISO3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code of the parent country    | 
| `fips_code`     | `varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL` |  ISO-3166-2 subdivision code for the state. Can be found in wikipedia articles such as this: [ISO_3166-2:NO](https://www.iso.org/sites/outage/#iso:code:3166:NO). [FIPS county codes](https://en.wikipedia.org/wiki/FIPS_county_code) were deprecated in 2008, so we are not using them |
| `iso2`          | `varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL` | Iso stuff stuff |
|  `type`         | `varchar(191) COLLATE utf8mb4_unicode_ci DEFAULT NULL` | Something |
| `latitude`      |`decimal(10,8) DEFAULT NULL` | Location from Google maps |
| `longitude`.    | `decimal(11,8) DEFAULT NULL` | Location from Google maps |
| `created_at`    | `timestamp NULL DEFAULT NULL` | `NOW()` |
| `updated_at`    | `timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP` | This is automatically set |
| `flag`          | `tinyint(1) NOT NULL DEFAULT '1'` | ??? |
| `wikiDataId`    |`varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL COMMENT 'Rapid API GeoDB Cities'` | The unique ID for this state on wikiData |
