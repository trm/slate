---
title: Vitae API Reference

language_tabs:
  - shell: cURL

includes:
  - errors

search: true
---

# Introduction

Welcome to ChronicleVitae's internal API documentation. This API is accessing back-end services and is not available for public consumption.

# Authentication

All requests must include an access token which can be obtained via a 2-legged oAuth request.

```shell
curl -X POST -d "grant_type=client_credentials" -d "client_id=<client_id>" \
    -d "client_secret=<client_secret>" \
    -d "scope=taxonomy" https://chroniclevitae.com/oauth/token?grant_type=client_credentials
```

> The above command returns JSON structured like this:

```json
{
    "access_token": "02c6863c7d088bceb5f000079a3960b5deee4c2e34fef4849a826a3434f78dcb",
    "created_at": 1438718376,
    "expires_in": 43200,
    "token_type": "bearer",
    "scopes": "taxonomy"
}
```

### HTTP Request

`POST https://chroniclevitae.com/oauth/token?grant_type=client_credentials`

<aside class="warning">
The taxonomy API is only available in version 2. All requests must include the header "Accept: application/vnd.vitae.v2"
</aside>

### POST Parameters

Parameter | Description
--------- | -----------
client_id | API client key
client_secret | API secret token
scope | Oauth scope <taxonomy>

# Taxonomy

## List Taxonomies

```shell
curl "https://chroniclevitae.com/api/taxonomy?limit=10&offset=5"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy?limit=10&offset=5",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 6,
            "name": "Synchronic linguistics",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 3,
                "name": "Anthropological linguistics",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_discipline_id": null,
            "child_disciplines": [
                {
                    "canonical_discipline_id": null,
                    "id": 9,
                    "name": "Economic anthropology",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 10,
                    "name": "Ethnography",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 11,
                    "name": "Ethnology",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 12,
                    "name": "Media anthropology",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 13,
                    "name": "Political anthropology",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 14,
                    "name": "Psychological anthropology",
                    "status": "accepted"
                }
            ],
            "id": 7,
            "name": "Cultural anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 2,
                "name": "Anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 8,
            "name": "Anthropology of religion",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 3,
                "name": "Anthropological linguistics",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 9,
            "name": "Economic anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 7,
                "name": "Cultural anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 10,
            "name": "Ethnography",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 7,
                "name": "Cultural anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 11,
            "name": "Ethnology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 7,
                "name": "Cultural anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 12,
            "name": "Media anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 7,
                "name": "Cultural anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 13,
            "name": "Political anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 7,
                "name": "Cultural anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 14,
            "name": "Psychological anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 7,
                "name": "Cultural anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        },
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [
                {
                    "canonical_discipline_id": null,
                    "id": 16,
                    "name": "Ecology and environment",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 17,
                    "name": "Forensic anthropology",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 18,
                    "name": "Gene-culture coevolution",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 19,
                    "name": "Human behavioral ecology",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 20,
                    "name": "Human evolution",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 21,
                    "name": "Medical anthropology",
                    "status": "accepted"
                }
            ],
            "id": 15,
            "name": "Physical anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 2,
                "name": "Anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        }
    ],
    "status": 200
}
```

This endpoint retrieves all taxonomies.

### HTTP Request

`GET https://chroniclevitae.com/api/taxonomy`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
limit | Limit number of results (optional)
offset | Offset to start listing results (optional)
recursive | Boolean flag to recurse child disciplines (default false)
status | Scope results by term's status [approved|pending] (optional)
roots | Only return root level terms and the first level of children (default false)
order_by_count | Order results by user count [true|false] (optional)


## Get Taxonomy

```shell
curl "https://chroniclevitae.com/api/taxonomy/3"
```

> The above command retrieves the discipline object for term 3. A valid request returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy/3",
    "results": [
        {
            "canonical_children": 1,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [
                {
                    "canonical_discipline_id": null,
                    "id": 4,
                    "name": "Diachronic linguistics",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 5,
                    "name": "Ethnolinguistics",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 6,
                    "name": "Synchronic linguistics",
                    "status": "accepted"
                },
                {
                    "canonical_discipline_id": null,
                    "id": 8,
                    "name": "Anthropology of religion",
                    "status": "accepted"
                }
            ],
            "id": 3,
            "name": "Anthropological linguistics",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 2,
                "name": "Anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        }
    ],
    "status": 200
}
```

This endpoint retrieves data for the specified taxonomy.

### HTTP Request

`GET https://chroniclevitae.com/api/taxonomy/<id>`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of taxonomy
recursive | Boolean flag to recurse child disciplines (default false)

## Get Taxonomy Aliases

```shell
curl "https://chroniclevitae.com/api/taxonomy/3/alias"
```

> The above command returns a list of non-canonical terms (i.e. alias/associations) pointing to term 3. A valid request returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy/3/alias",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": 3,
            "child_disciplines": [],
            "id": 2025,
            "name": "History preservation studies",
            "parent_discipline": null,
            "status": "accepted"
        }
    ],
    "status": 200
}


```

This endpoint retrieves a listing of aliases and associations for the specified taxonomy.

### HTTP Request

`GET https://chroniclevitae.com/api/taxonomy/<id>/alias`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of taxonomy
recursive | Boolean flag to recurse child disciplines (default false)

## Delete Taxonomy

This endpoint deletes the specified taxonomy item.

### HTTP Request

`DELETE https://chroniclevitae.com/api/taxonomy/<id>`

<aside class="success">
Successful requests will return HTTP status 204
</aside>
<aside class="warning">
Taxonomies with associated users as well as top level taxonomies with child taxonomies cannot be deleted and will return HTTP status 422
</aside>
<aside class="warning">
When deleting a mid-level taxonomy that has child taxonomies those children will be reassigned to the parent of the deleted taxonomy
</aside>

### DELETE Parameters

Parameter | Description
--------- | -----------
id | ID of taxonomy to delete

## Create Taxonomy

```shell
curl -X POST -d "discipline[name]=Ancient studies" -d "discipline[status]=accepted" \
    -d "discipline[parent_relation][parent_discipline_id]=2" "https://chroniclevitae.com/api/taxonomy"
```

> The above command will create a new taxonomy called 'Ancient studies' with parent/child relationships. A valid request returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 3036,
            "name": "Ancient studies",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 2,
                "name": "Anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        }
    ],
    "status": 200
}
```

This endpoint creates a new taxonomy entry with parent/child relationships (if specified).

### HTTP Request

`POST https://chroniclevitae.com/api/taxonomy`

<aside class="success">
Successful requests will return HTTP status 200
</aside>
<aside class="warning">
Taxonomy name must be unique. An HTTP 422 will be returned if a taxonomy with the specified name already exists.
</aside>

### POST Parameters

Parameter | Description
--------- | -----------
discipline[name] | Taxonomy name
discipline[canonical_discipline_id] | ID of canonical taxonomy (optional)
discipline[status] | Taxonomy status (optional)
discipline[parent_relation][parent_discipline_id] | ID of parent taxonomy (optional)


## Update Taxonomy

```shell
curl -X PUT -d "discipline[parent_relation][parent_discipline_id]=3048" -d "discipline[status]=accepted" https://chroniclevitae.com/api/taxonomy/3046"
```

> The above command attempts to update term 3046's status from pending to accepted and change its parent discipline from 'Ancient studies' to 'Ancient anthropology'. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/3048",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [
                {
                    "canonical_discipline_id": null,
                    "id": 3033,
                    "name": "Egyptian hieroglyphics",
                    "status": "pending"
                }
            ],
            "id": 3046,
            "name": "Historical anthropology",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 3048,
                "name": "Ancient anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        }
    ],
    "status": 200
}

```

This endpoint is used to update attributes and relationships on an existing taxonomy.

### HTTP Request

`PUT https://chroniclevitae.com/api/taxonomy/<id>`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### PUT Parameters

Parameter | Description
--------- | -----------
discipline[status] | Taxonomy status (optional)
discipline[canonical_discipline_id] | ID of canonical taxonomy (optional)
discipline[parent_relation][parent_discipline_id] | ID of parent taxonomy (optional)


## Rename Taxonomy

```shell
curl -X PUT -d "discipline[name]=Life studies" https://chroniclevitae.com/api/taxonomy/3048/rename"
```

> The above command attempts to update term 3048's name from 'Ancient anthropology' to 'Life studies'. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/3048/rename",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [
                {
                    "canonical_discipline_id": null,
                    "id": 3033,
                    "name": "Egyptian hieroglyphics",
                    "status": "pending"
                }
            ],
            "id": 3048,
            "name": "Life studies",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 2,
                "name": "Anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        }
    ],
    "status": 200
}

```

This endpoint is used to rename an existing term.

### HTTP Request

`PUT https://chroniclevitae.com/api/taxonomy/<id>/rename`

<aside class="success">
Successful requests will return HTTP status 200
</aside>
<aside class="notice">
When renaming without the force param a new taxonomy term will be created under the specified name and the existing term will be demoted and have a canonical reference to the new term. If a term already exist with the specified name the existing term will be demoted and have a canonical reference to that term.
</aside>
<aside class="notice">
Force is implied if changes only affect a term's capitalization. In this case the existing term will be updated rather than create a new term.
</aside>

### PUT Parameters

Parameter | Description
--------- | -----------
discipline[name] | Taxonomy name (optional)
force | Force an update to the existing term rather than create a new canonical term if users exist on term



## Demote Taxonomy

```shell
curl -X PUT -d "discipline[canonical_discipline_id]=2654" https://chroniclevitae.com/api/taxonomy/3048/demote"
```

> The above command demotes term 3048 from a canonical to non-canonical (i.e. alias/association) term. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/3048/demote",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": 2654,
            "child_disciplines": [],
            "id": 3048,
            "name": "Life studies",
            "parent_discipline": {},
            "status": "accepted"
        }
    ],
    "status": 200
}

```

This endpoint is used to demote a canonical term to a non-canonical (i.e. alias/association) term.

### HTTP Request

`PUT https://chroniclevitae.com/api/taxonomy/<id>/demote`

<aside class="success">
Successful requests will return HTTP status 200
</aside>
<aside class="warning">
Only mid-level terms can be demoted. If the term does have a parent discipline and has children a 422 error status will be returned.
</aside>
<aside class="notice">
If a canonical discipline ID is not provided the term's parent discipline will be used instead.
</aside>
<aside class="notice">
If the term has child disciplines those terms will be reassigned to the term's parent discipline prior to demoting.
</aside>

### PUT Parameters

Parameter | Description
--------- | -----------
discipline[canonical_discipline_id] | ID of canonical discipline to point to
discipline[status] | Update term's status (optional)

## Promote Taxonomy

```shell
curl -X PUT -d "discipline[parent_relation][parent_discipline_id]=2" https://chroniclevitae.com/api/taxonomy/3048/promote"
```

> The above command promotes term 3048 from a non-canonical to canonical term. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/3048/promote",
    "results": [
        {
            "canonical_children": 0,
            "total_users": 0,
            "canonical_discipline_id": null,
            "child_disciplines": [],
            "id": 3048,
            "name": "Life studies",
            "parent_discipline": {
                "canonical_discipline_id": null,
                "id": 2,
                "name": "Anthropology",
                "status": "accepted"
            },
            "status": "accepted"
        }
    ],
    "status": 200
}

```

This endpoint is used to promote a non-canonical (i.e. alias/association) term to a canonical term.

### HTTP Request

`PUT https://chroniclevitae.com/api/taxonomy/<id>/promote`

<aside class="success">
Successful requests will return HTTP status 200
</aside>
<aside class="notice">
If a parent discipline ID is not provided the term's canonical discipline will be used instead.
</aside>


### PUT Parameters

Parameter | Description
--------- | -----------
discipline[parent_relation][parent_discipline_id] | ID of parent discipline (optional)
discipline[status] | Update term's status (optional)


## Search Taxonomy

```shell
curl -X GET https://chroniclevitae.com/api/taxonomy/search?term=biology"
```

> The above command performs a search against all taxonomies. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/search?term=biology",
    "results": [
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:35.000-04:00",
            "id": 282,
            "name": "Psychobiology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:35.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:35.000-04:00",
            "id": 288,
            "name": "Conservation biology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:35.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:36.000-04:00",
            "id": 365,
            "name": "Sociobiology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:36.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:41.000-04:00",
            "id": 666,
            "name": "Philosophy of biology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:41.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:51.000-04:00",
            "id": 1210,
            "name": "Chemical biology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:51.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:52.000-04:00",
            "id": 1246,
            "name": "Astrobiology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:52.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:54.000-04:00",
            "id": 1407,
            "name": "Computational biology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:54.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:54.000-04:00",
            "id": 1410,
            "name": "Cryobiology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:54.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:54.000-04:00",
            "id": 1413,
            "name": "Population biology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:54.000-04:00"
        },
        {
            "canonical_discipline_id": null,
            "created_at": "2015-03-27T14:17:54.000-04:00",
            "id": 1414,
            "name": "Wildlife biology",
            "status": "accepted",
            "updated_at": "2015-03-27T14:17:54.000-04:00"
        }
    ],
    "status": 200
}

```

This endpoint is used to search for a taxonomy by name.

### HTTP Request

`GET https://chroniclevitae.com/api/taxonomy/search?term=<search_term>`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### GET Parameters

Parameter | Type | Required | Default | Description
--------- | ---- | -------- | ------- | --------
term | String | Y | | Name of term to be searched
status | String| N | accepted | Scope results to specified status (pending/accepted)
order_by_count | Boolean | N | false | Order results by user count
roots | Boolean | false | Scope results to only root-level canonical terms
canonical | Boolean | nil | Scope results to only canonical terms
rootpending | Boolean | false | Scope results to only root-level pending terms


## Taxonomy Parent List

```shell
curl -X GET https://chroniclevitae.com/api/taxonomy/178/parent_ids"
```

> The above command returns an array containing the term 178's parent IDs in ascending order up the taxonomy tree. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/178/parent_ids",
    "results": [
        177,
        176,
        173,
        1
    ],
    "status": 200
}

```

This endpoint is used to list the term's parent IDs in ascending order.

### HTTP Request

`GET https://chroniclevitae.com/api/taxonomy/<id>/parent_ids`

<aside class="success">
Successful requests will return HTTP status 200
</aside>
