# ![LOGO](logo.png) TheTVDB API v2 **flow**ground Connector

## Description

A generated **flow**ground connector for the TheTVDB API v2 API (version 2.2.0).

Generated from: https://api.apis.guru/v2/specs/thetvdb.com/2.2.0/swagger.json<br/>
Generated at: 2019-05-07T17:44:24+03:00

## API Description

API v2 targets v1 functionality with a few minor additions. The API is accessible via https://api.thetvdb.com and provides the following REST endpoints in JSON format.


How to use this API documentation
----------------


You may browse the API routes without authentication, but if you wish to send requests to the API and see response data, then you must authenticate.
1. Obtain a JWT token by `POST`ing  to the `/login` route in the `Authentication` section with your API key and credentials.
1. Paste the JWT token from the response into the "JWT Token" field at the top of the page and click the 'Add Token' button.


You will now be able to use the remaining routes to send requests to the API and get a response.


Language Selection
----------------


Language selection is done via the `Accept-Language` header. At the moment, you may only pass one language abbreviation in the header at a time. Valid language abbreviations can be found at the `/languages` route..


Authentication
----------------


Authentication to use the API is similar to the How-to section above. Users must `POST` to the `/login` route with their API key and credentials in the following format in order to obtain a JWT token.

`{"apikey":"APIKEY","username":"USERNAME","userkey":"USERKEY"}`

Note that the username and key are ONLY required for the `/user` routes. The user's key is labled `Account Identifier` in the account section of the main site.
The token is then used in all subsequent requests by providing it in the `Authorization` header. The header will look like: `Authorization: Bearer <yourJWTtoken>`. Currently, the token expires after 24 hours. You can `GET` the `/refresh_token` route to extend that expiration date.


Versioning
----------------


You may request a different version of the API by including an `Accept` header in your request with the following format: `Accept:application/vnd.thetvdb.v$VERSION`. This documentation automatically uses the version seen at the top and bottom of the page.

## Authorization

Supported authorization schemes:
- API Key
## Actions

### Returns the full information for a given episode id. __Deprecation Warning:__ The _director_ key will be deprecated in favor of the new _directors_ key in a future release.

*Tags:* `Episodes`

#### Input Parameters
* `id` - _required_ - ID of the episode
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### All available languages. These language abbreviations can be used in the `Accept-Language` header for routes that return translation records.

*Tags:* `Languages`

### Information about a particular language, given the language ID.

*Tags:* `Languages`

#### Input Parameters
* `id` - _required_ - ID of the language

### Returns a session token to be included in the rest of the requests. Note that API key authentication is required for all subsequent requests and user auth is required for routes in the `User` section

*Tags:* `Authentication`

### Refreshes your current, valid JWT token and returns a new token. Hit this route so that you do not have to post to `/login` with your API key and credentials once you have already been authenticated.

*Tags:* `Authentication`

### Allows the user to search for a series based on the following parameters.

*Tags:* `Search`

#### Input Parameters
* `name` - _optional_ - Name of the series to search for.
* `imdbId` - _optional_ - IMDB id of the series
* `zap2itId` - _optional_ - Zap2it ID of the series to search for.
* `slug` - _optional_ - Slug from site URL of series (https://www.thetvdb.com/series/$SLUG)
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns an array of parameters to query by in the `/search/series` route.

*Tags:* `Search`

### Returns a series records that contains all information known about a particular series id.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns header information only about the given series ID.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns actors for the given series id

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series

### All episodes for a given series. Paginated with 100 results per page.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `page` - _optional_ - Page of results to fetch. Defaults to page 1 if not provided.

### This route allows the user to query against episodes for the given series. The response is a paginated array of episode records.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `absoluteNumber` - _optional_ - Absolute number of the episode
* `airedSeason` - _optional_ - Aired season number
* `airedEpisode` - _optional_ - Aired episode number
* `dvdSeason` - _optional_ - DVD season number
* `dvdEpisode` - _optional_ - DVD episode number
* `imdbId` - _optional_ - IMDB id of the series
* `page` - _optional_ - Page of results to fetch. Defaults to page 1 if not provided.
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns the allowed query keys for the `/series/{id}/episodes/query` route

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series

### Returns a summary of the episodes and seasons available for the series.<br/>
> <br/>
> __Note__: Season "0" is for all episodes that are considered to be specials.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series

### Returns a series records, filtered by the supplied comma-separated list of keys. Query keys can be found at the `/series/{id}/filter/params` route.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `keys` - _required_ - Comma-separated list of keys to filter by
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns the list of keys available for the `/series/{id}/filter` route

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns a summary of the images for a particular series

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Query images for the given series ID.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `keyType` - _optional_ - Type of image you're querying for (fanart, poster, etc. See ../images/query/params for more details).
* `resolution` - _optional_ - Resolution to filter by (1280x1024, for example)
* `subKey` - _optional_ - Subkey for the above query keys. See /series/{id}/images/query/params for more information
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns the allowed query keys for the `/series/{id}/images/query` route. Contains a parameter record for each unique `keyType`, listing values that will return results.

*Tags:* `Series`

#### Input Parameters
* `id` - _required_ - ID of the series
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns an array of series that have changed in a maximum of one week blocks since the provided `fromTime`.<br/>
> <br/>
> <br/>
> The user may specify a `toTime` to grab results for less than a week. Any timespan larger than a week will be reduced down to one week automatically.

*Tags:* `Updates`

#### Input Parameters
* `fromTime` - _required_ - Epoch time to start your date range.
* `toTime` - _optional_ - Epoch time to end your date range. Must be one week from `fromTime`.
* `Accept-Language` - _optional_ - Records are returned with the Episode name and Overview in the desired language, if it exists. If there is no translation for the given language, then the record is still returned but with empty values for the translated fields.

### Returns an array of valid query keys for the `/updated/query/params` route.

*Tags:* `Updates`

### Returns basic information about the currently authenticated user.

*Tags:* `Users`

### Returns an array of favorite series for a given user, will be a blank array if no favorites exist.

*Tags:* `Users`

### Deletes the given series ID from the user's favorite's list and returns the updated list.

*Tags:* `Users`

#### Input Parameters
* `id` - _required_ - ID of the series

### Adds the supplied series ID to the user's favorite's list and returns the updated list.

*Tags:* `Users`

#### Input Parameters
* `id` - _required_ - ID of the series

### Returns an array of ratings for the given user.

*Tags:* `Users`

### Returns an array of ratings for a given user that match the query.

*Tags:* `Users`

#### Input Parameters
* `itemType` - _optional_ - Item to query. Can be either 'series', 'episode', or 'banner'

### Returns a list of query params for use in the `/user/ratings/query` route.

*Tags:* `Users`

### This route deletes a given rating of a given type.

*Tags:* `Users`

#### Input Parameters
* `itemType` - _required_ - Item to update. Can be either 'series', 'episode', or 'image'
* `itemId` - _required_ - ID of the ratings record that you wish to modify

### This route updates a given rating of a given type.

*Tags:* `Users`

#### Input Parameters
* `itemType` - _required_ - Item to update. Can be either 'series', 'episode', or 'image'
* `itemId` - _required_ - ID of the ratings record that you wish to modify
* `itemRating` - _required_ - The updated rating number

## License

**flow**ground :- Telekom iPaaS / thetvdb-com-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
