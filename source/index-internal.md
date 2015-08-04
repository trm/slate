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
curl -X POST -d "grant_type=client_credentials" -d "client_id=<client_id>" -d "client_secret=<client_secret>" https://chroniclevitae.com/oauth/token
```

> The above command returns JSON structured like this:

```json
{
    "access_token": "02c6863c7d088bceb5f000079a3960b5deee4c2e34fef4849a826a3434f78dcb",
    "created_at": 1438718376,
    "expires_in": 43200,
    "token_type": "bearer"
}
```

### HTTP Request

`POST https://chroniclevitae.com/oauth/token`

<aside class="warning">
You must first obtain an API client key along with your secret token in order to authenticate.
</aside>

### POST Parameters

Parameter | Description
--------- | -----------
grant_type | client_credentials
client_id | API client key
client_secret | API secret token

# Taxonomy

## Get All Taxonomies

```shell
curl "https://chroniclevitae.com/api/taxonomy?limit=10&offset=5"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy?limit=10&offset=5",
    "results": [
        {
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

## Get Taxonomy

```shell
curl "https://chroniclevitae.com/api/taxonomy/3"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy/3",
    "results": [
        {
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
curl -X POST -d "discipline[name]=Ancient studies" -d "discipline[status]=accepted" -d "discipline[parent_relation][parent_discipline_id]=2" -d "discipline[child_relation][children][]=3033" "https://chroniclevitae.com/api/taxonomy"
```

> The above command will create a new taxonomy called 'Ancient studies' with parent/child relationships. A valid request returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/taxonomy",
    "results": [
        {
            "canonical_discipline_id": null,
            "child_disciplines": [
                {
                    "canonical_discipline_id": null,
                    "id": 3033,
                    "name": "Egyptian hieroglyphics",
                    "status": "accepted"
                }
            ],
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
discipline[child_relation][inherit_children_from] | Inherit child taxonomies from specified taxonomy id (optional)
discipline[child_relation][children][] | List of child taxonomy IDs (optional)

## Update Taxonomy

```shell
curl -X PUT -d "discipline[name]=Ancient anthropology" "https://chroniclevitae.com/api/taxonomy/3036"
```

> The above command attempts to update the taxonomy entry's name from 'Ancient studies' to 'Ancient anthropology'. A valid request returns JSON structured like this:

```json
{
    "href": "http://127.0.0.1:3000/api/taxonomy/3036",
    "results": [
        {
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
            "name": "Ancient anthropology",
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

This endpoint updates an existing taxonomy according to the attributes specified.

### HTTP Request

`PUT https://chroniclevitae.com/api/taxonomy`

<aside class="success">
Successful requests will return HTTP status 200
</aside>
<aside class="warning">
When renaming, a new taxonomy entry will be created under the new name (or existing taxonomy if such exists) and the existing taxonomy will have a canonical reference to the new term.
</aside>

### PUT Parameters

Parameter | Description
--------- | -----------
discipline[name] | Taxonomy name (optional)
discipline[canonical_discipline_id] | ID of canonical taxonomy (optional)
discipline[status] | Taxonomy status (optional)
discipline[parent_relation][parent_discipline_id] | ID of parent taxonomy (optional)
discipline[child_relation][inherit_children_from] | Inherit child taxonomies from specified taxonomy id (optional)
discipline[child_relation][children][] | List of child taxonomy IDs (optional)
