---
title: Vitae API Reference

language_tabs:
  - shell: cURL

toc_footers:
  - <a href='mailto:support@chroniclevitae.com?subject=API Developer Key'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to ChronicleVitae's API documentation.

Vitae uses oAuth to authenticate API requests. Users must authenticate their accounts and will recieve an oAuth access token which must be included with all requests. All responses are returned in JSON format.

# Authentication

oAuth authentication can be initiated at https://chroniclevitae.com/authorize followed by redirecting the user to https://chroniclevitae.com/application_login.

# Users

## Get User

```shell
curl "https://chroniclevitae.com/api/users/self"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/users/self?access_token=<access_token>",
    "results": [
        {
            "country": "US",
            "current_employer": "Georgetown University",
            "current_position": "Director of Music",
            "current_position_type": "Graduate/PhD student or Post-Doc",
            "degree_groups": [
                {
                    "degrees": [
                        {
                            "field_of_study": "Choral conducting",
                            "name": "Masters of Music Performance",
                            "year": 2010
                        },
                        {
                            "field_of_study": "Voice",
                            "name": "Bachelor of Music Education",
                            "year": 2013
                        }
                    ],
                    "institution": "University of Maryland, College Park"
                }
            ],
            "display_name": "John Smith",
            "first_name": "John",
            "last_name": "Scott",
            "email": "jsmith@chronicle.com",
            "id": 9999999,
            "job_application_information_present": true,
            "job_application_questionnaire": {
                "address_1": "1255 23rd Street, NW",
                "address_2": "Apt. 203",
                "alternative_phone": "202-555-9874",
                "city": "Washington",
                "country": "United States",
                "primary_phone": "202-466-1000",
                "state": "DC",
                "zip_code": "20037"
            },
            "position_groups": [
                {
                    "employer": "Smith's School of Music",
                    "positions": [
                        {
                            "end_month": 5,
                            "end_year": 2014,
                            "is_current": false,
                            "name": "Voice Faculty Member",
                            "start_month": 12,
                            "start_year": 2013
                        }
                    ]
                },
                {
                    "employer": "Johnstown College",
                    "positions": [
                        {
                            "end_month": 5,
                            "end_year": 2014,
                            "is_current": false,
                            "name": "Choral Graduate Assistant",
                            "start_month": 5,
                            "start_year": 2013
                        }
                    ]
                },
                {
                    "employer": "Bocelli School of Music",
                    "positions": [
                        {
                            "end_month": null,
                            "end_year": null,
                            "is_current": true,
                            "name": "Interim Professor of Music",
                            "start_month": 5,
                            "start_year": 2014
                        }
                    ]
                },
            ],
            "references": [
                {
                    "first_name": "Jeff",
                    "last_name": "Bruns",
                    "email_address": "jbruns123@chronicle.com",
                    "phone_number": "410-555-6658",
                    "relationship": "Manager",
                    "address_1": "1355 14th Street, NW"
                    "address_2": "STE 455",
                    "city": "Washington",
                    "state": "DC"
                    "zip_code": "20022"
                }
            ],
            "zip_code": "20037"
        }
    ],
    "status": 200
}


```

This endpoint retrieves account data for the authenticated user.

### HTTP Request

`GET https://chroniclevitae.com/api/users/self`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

# Dossier

## Get Dossier

```shell
curl "https://chroniclevitae.com/api/dossier/self"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/dossier/self",
    "results": [
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/999888777/download",
                    "filename": "Teaching_philosophy_2004_20150d87s5.docx",
                    "id": 999888777,
                    "name": "Teaching philosophy 2004.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:45:23-04:00"
                },
                {
                    "download_url": "https://chroniclevitae.com/api/documents/998875874/download",
                    "filename": "Professional_Teaching_Goals.docxas8f65st.docx",
                    "id": 998875874,
                    "name": "Professional Teaching Goals.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:45:42-04:00"
                },
                {
                    "download_url": "https://chroniclevitae.com/api/documents/559718754/download",
                    "filename": "Teaching_Methods.docx2sdjsdf-sd7sdgmb.docx",
                    "id": 559718754,
                    "name": "Teaching Methods.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:45:56-04:00"
                }
            ],
            "folders": [],
            "id": 22248920145,
            "name": "Teaching Statements"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/55972642/download",
                    "filename": "webpresentation.pptx20150509-29668-ov1dwh.pptx",
                    "id": 55972642,
                    "name": "webpresentation.pptx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:51:19-04:00"
                },
                {
                    "download_url": "https://chroniclevitae.com/api/documents/5994712874252/download",
                    "filename": "BC_Skills_Evaluations.pptx20s5sd85s-asd5trbf4-1j788fj.pptx",
                    "id": 5994712874252,
                    "name": "BC Skills Evaluations.pptx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:52:29-04:00"
                }
            ],
            "folders": [],
            "id": 288600145,
            "name": "Presentations"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/26971556561/download",
                    "filename": "Cover_Letter_Southeastern.docx20150509-25s8-a455f25drd.docx",
                    "id": 26971556561,
                    "name": "Cover Letter Southeastern.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T15:03:26-04:00"
                }
            ],
            "folders": [],
            "id": 20023680,
            "name": "Cover Letters"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/298423125/download",
                    "filename": "cvfolio_final.pdf20150509-29ljgp8-668q.pdf",
                    "id": 298423125,
                    "name": "cvfolio final.pdf",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:44:43-04:00"
                }
            ],
            "folders": [],
            "id": 523358741,
            "name": "CVs"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/212687400247/download",
                    "filename": "MD_License__NREMTP_Certification.pdf20150509-1558d8d2-14s58f8ds4a.pdf",
                    "id": 212687400247,
                    "name": "MD License & NREMTP Certification.pdf",
                    "tag_list": [],
                    "updated_at": "2015-05-09T10:31:55-04:00"
                }
            ],
            "folders": [],
            "id": 3314321,
            "name": "Other"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/2102481005/download",
                    "filename": "References_list.docx20150509-15650524-16dsd8tysw.docx",
                    "id": 2102481005,
                    "name": "References list.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T13:32:05-04:00"
                }
            ],
            "folders": [],
            "id": 3314319,
            "name": "Research Statements"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/22587469024/download",
                    "filename": "Book_Chapter___Evaluation_of_Simulation_in_Nursing_using_Rubrics.docx20150509-12558303-giadfs.docx",
                    "id": 22587469024,
                    "name": "Book Chapter   Evaluation of Simulation in Nursing using Rubrics.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:48:02-04:00"
                }
            ],
            "folders": [],
            "id": 26902425874,
            "name": "Writing Samples"
        },
        {
            "documents": [
                {
                    "download_url": "https://chroniclevitae.com/api/documents/22974598/download",
                    "filename": "Nursing_Skills_Training_Evaluation.docx20150509-1548s703-gisdadfs.docx",
                    "id": 22974598,
                    "name": "Evaluation of Simulation in Nursing Training.docx",
                    "tag_list": [],
                    "updated_at": "2015-05-09T09:48:02-04:00"
                }
            ],
            "folders": [],
            "id": 228742574,
            "name": "Publications"
        }
    ],
    "status": 200
}


```

This endpoint retrieves a list of all dossier documents for the authenticated user

### HTTP Request

`GET https://chroniclevitae.com/api/dossier/self`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

# Documents

## Download a Document

This endpoint downloads a raw document from the user's dossier list

```shell
curl "https://chroniclevitae.com/api/documents/<id>/download?access_token=<access_token>"
```

### HTTP Request

`GET https://chroniclevitae.com/api/documents/<id>/download?access_token=<access_token>`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
id | Document ID

## Upload a Document

This endpoint uploads a multipart document into the user's dossier

```shell
curl --form "document=@My_File_Upload.docx" --form "folder=9927" "https://chroniclevitae.com/api/documents/upload?access_token=<access_token>"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/documents/upload?access_token=<access_token>",
    "results": [
        {
            "download_url": "https://chroniclevitae.com/api/documents/998218960/download",
            "filename": "My_File_Upload.docx20150727-138s9s6-1cfz5q0.docx",
            "id": 998218960,
            "name": "Tanya My_File_Upload.docx",
            "tag_list": [],
            "updated_at": "2015-07-27T13:23:49-04:00"
        }
    ],
    "status": 201
}

```

### HTTP Request

`POST https://chroniclevitae.com/api/documents/upload?access_token=<access_token>`

<aside class="success">
Successful requests will return HTTP status 201
</aside>

### POST Parameters

Parameter | Description
--------- | -----------
document | Raw data of document to be uploaded
folder_id | ID of folder to upload into (optional)

# Recommendation Letters

## List Recommendation Letters

This endpoint lists all recommendation letters for the authenticated user

```shell
curl "https://chroniclevitae.com/api/recommendation_letters?access_token=<access_token>"
```

> The above command returns JSON structured like this:

```json
{
    "href": "https://chroniclevitae.com/api/recommendation_letters?access_token=<access_token>",
    "results": [
        {
            "id": 9983264930,
            "title": "Recommendation letter from Dr. Jones",
            "filename": "Jones_Recommendation_Letter.docx20150727-138s9s6-1cfz5q0.docx",
            "download_url": "https://chroniclevitae.com/api/documents/9983264930/download",
            "updated_at": "2015-07-27T13:23:49-04:00"
        },
        {
            "id": 883649378,
            "title": "Recommendation letter from Dr. Smith",
            "filename": "Smith_Recommendation_Letter.docx20150727-138s9s6-1cfz5q0.docx",
            "download_url": "https://chroniclevitae.com/api/documents/883649378/download",
            "updated_at": "2015-07-29T11:14:12-04:00"
        }
    ],
    "status": 200
}
```

### HTTP Request

`GET https://chroniclevitae.com/api/recommendation_letters?access_token=<access_token>`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

## Download Recommendation Letter

This endpoint downloads the specified recommendation letter for the authenticated user

```shell
curl "https://chroniclevitae.com/api/recommendation_letters/<id>/download?access_token=<access_token>"
```

### HTTP Request

`POST https://chroniclevitae.com/api/recommendation_letters/<id>/download?access_token=<access_token>`

<aside class="success">
Successful requests will return HTTP status 200
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
id | Recommendation letter ID
