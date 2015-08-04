---
title: Vitae API Reference

language_tabs:
  - shell: cURL

includes:
  - errors

search: true
---

# Introduction

Welcome to ChronicleVitae's internal API documentation.

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

```shell
curl -X DELETE "https://chroniclevitae.com/api/taxonomy/3045"
```

> The above command returns JSON structured like this:

```json

```

This endpoint retrieves account data for the authenticated user.

### HTTP Request

`DELETE https://chroniclevitae.com/api/taxonomy/<id>`

<aside class="success">
Successful requests will return HTTP status 204
</aside>

### DELETE Parameters

Parameter | Description
--------- | -----------
id | ID of taxonomy to delete

## Create Taxonomy

```shell
curl -X POST -d "discipline[name]=" https://chroniclevitae.com/api/taxonomy"
```

> The above command returns JSON structured like this:

```json

```

This endpoint retrieves account data for the authenticated user.

### HTTP Request

`POST https://chroniclevitae.com/api/taxonomy`

### POST Parameters

Parameter | Description
--------- | -----------
discipline[name] | Taxonomy name
discipline[canonical_discipline_id] | ID of canonical taxonomy (optional)
discipline[status] | Taxonomy status (optional)
discipline[parent_relation][parent_discipline_id] | ID of parent taxonomy (optional)
discipline[child_relation][inherit_children_from] | Inherit child taxonomies from specified taxonomy id (optional)
discipline[child_relation][children][] | List of child taxonomies (optional)

## Update Taxonomy

```shell
curl -X PUT -d "id=3000" "https://chroniclevitae.com/api/taxonomy"
```

> The above command returns JSON structured like this:

```json

```

This endpoint retrieves account data for the authenticated user.

### HTTP Request

`PUT https://chroniclevitae.com/api/taxonomy`

### PUT Parameters

Parameter | Description
--------- | -----------
discipline[name] | Taxonomy name (optional)
discipline[canonical_discipline_id] | ID of canonical taxonomy (optional)
discipline[status] | Taxonomy status (optional)
discipline[parent_relation][parent_discipline_id] | ID of parent taxonomy (optional)
discipline[child_relation][inherit_children_from] | Inherit child taxonomies from specified taxonomy id (optional)
discipline[child_relation][children][] | List of child taxonomies (optional)
