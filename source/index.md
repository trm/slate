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

Vitae uses oAuth to authenticate API requests. Users must authenticate their accounts and will recieve an oAuth access token which must be included with all future requests. All responses are returned in JSON format.

<aside class="info">
Our latest API version is v2 and all requests should be made to this version. All API requests should include the header "Accept: application/vnd.vitae.v2"
</aside>

# Authentication

All requests must include an access token which can be obtained via a 3-legged oAuth request.

```shell
curl "https://chroniclevitae.com/oauth/authorize?response_type=code& \
      client_id=d08834fef4849a826a3434bceb5f000079a396f78dcb0b5deee4c2e02c6863c7& \
      redirect_uri=https://partner-site.com/oauth_redirect& \
      scope=user+document+dossier+lor& \
      state=027d088bceb5f000079ac6863c3960b5deee4c2e33434f78dcb"
```

> The above command returns an HTTP 302 status, redirecting to the Vitae login page for user authentication. Following successful user authentication an HTTP 302 status will be returned, redirecting the user's browser to the previously specified partner redirect URI with an oAuth code:

```code
HTTP/1.1 302 Found
Location: https://your-site.com/oauth_redirect?code=55af1845b26c8c442dde64bc4dfa870ebba779e371b333f27382e7ab814ac70d&state=21267c98-0fb0-48d9-ba93-c2fa9ce532b2
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache
X-Meta-Request-Version: 0.3.4
X-Request-Id: a836e76d-e6c7-42e5-8fee-c48a071067f5
X-Runtime: 0.065458
Date: Wed, 11 Nov 2015 23:02:04 GMT
Content-Length: 219
Connection: Keep-Alive
```

```shell
curl -X POST -d "grant_type=authorization_code" \
             -d "client_id=d08834fef4849a826a3434bceb5f000079a396f78dcb0b5deee4c2e02c6863c7" \
             -d "client_secret=26a3434bceb5f000079a396f78dcb0b5deee4c2e02c6863c7d08834fef4849a8"
             -d "code=55af1845b26c8c442dde64bc4dfa870ebba779e371b333f27382e7ab814ac70d"
             -d "redirect_uri=https://partner-site.com/oauth_redirect" \
             "https://chroniclevitae.com/oauth/token"
```

> The above command completes the oAuth workflow and if successful, will return a JSON response with your access token:

```json
{
    "access_token": "9e11b4c73ecda728c78792397622f917edb2f8ddca60dc27e10e75545d726b8f",
    "created_at": 1447355423,
    "expires_in": 43200,
    "refresh_token": "1b6faef4f8064185ad313abb69e1c53d696a3d22e92e04e231c64186d6fb424f",
    "scope": "user document dossier lor",
    "token_type": "bearer"
}

```

### Step 1 - oAuth Code Request

`GET https://chroniclevitae.com/oauth/authorize?response_type=code&client_id=<client_id>&redirect_uri=<redirect_uri>&scope=<scopes>&state=<client_state>`

### GET Parameters

Parameter | Description
--------- | -----------
client_id | API client key
redirect_uri | Partner's oauth redirect URI
response_type | oAuth requested response type (code)
scope | oAuth scopes (associated with your developer account during registration)
state | Optional value to include in oAuth response for session tracking

<aside class="success">
A successful request will return an HTTP 302 status, redirecting to the Vitae login page for user authentication. Following successful user authentication an HTTP 302 status will be returned, redirecting the user’s browser to the previously specified partner redirect URI with an oAuth code.
</aside>

### Step 2 - oAuth Token Request

`POST -d https://chroniclevitae.com/oauth/token`

### POST Parameters

Parameter | Description
--------- | -----------
client_id | API client key
client_secret | API secret
code | oAuth code returned in step 1
grant_type | oAuth grant type requested (authorization_code)
redirect_uri | Partner's oauth redirect URI

<aside class="success">
A successful request will return HTTP status 200 with a JSON response containing the oAuth access token.
</aside>

# Users

## Get User

```shell
curl -H "Accept: application/vnd.vitae.v2" "https://chroniclevitae.com/api/users/self"
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
                            "year": 2010,
                            "id": 96634,
                            "updated_at": "2016-03-04T10:34:13"
                        },
                        {
                            "field_of_study": "Voice",
                            "name": "Bachelor of Music Education",
                            "year": 2013,
                            "id": 96854,
                            "updated_at": "2016-03-04T10:34:13"
                        }
                    ],
                    "institution": "University of Maryland, College Park",
                    "id": 22515,
                    "updated_at": "2016-03-04T10:34:13"
                }
            ],
            "display_name": "John Smith",
            "first_name": "John",
            "last_name": "Scott",
            "email": "jsmith@chronicle.com",
            "user_url": "https://chroniclevitae.com/people/325874-john-smith/profile",
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
                    "id": 29938,
                    "updated_at": "2016-03-04T10:34:13",
                    "employer": "Smith's School of Music",
                    "positions": [
                        {
                            "id": 2593,
                            "updated_at": "2016-03-04T10:34:13",
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
                    "id": 33574,
                    "updated_at": "2016-03-04T10:34:13",
                    "employer": "Johnstown College",
                    "positions": [
                        {
                            "id": 11678,
                            "updated_at": "2016-03-04T10:34:13",
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
                    "id": 33524,
                    "updated_at": "2016-03-04T10:34:13",
                    "employer": "Bocelli School of Music",
                    "positions": [
                        {
                            "id": 38829,
                            "updated_at": "2016-03-04T10:34:13",
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
                    "id": 12984,
                    "updated_at": "2016-03-04T10:34:13",
                    "first_name": "Jeff",
                    "last_name": "Bruns",
                    "email_address": "jbruns123@chronicle.com",
                    "phone_number": "410-555-6658",
                    "relationship": "Manager",
                    "address_1": "1355 14th Street, NW",
                    "address_2": "STE 455",
                    "city": "Washington",
                    "state": "DC",
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
curl -H "Accept: application/vnd.vitae.v2" "https://chroniclevitae.com/api/dossier/self"
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
curl -H "Accept: application/vnd.vitae.v2" "https://chroniclevitae.com/api/documents/<id>/download?access_token=<access_token>"
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
curl -H "Accept: application/vnd.vitae.v2" --form "document=@My_File_Upload.docx" --form "folder=9927" "https://chroniclevitae.com/api/documents/upload?access_token=<access_token>"
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
curl -H "Accept: application/vnd.vitae.v2" "https://chroniclevitae.com/api/recommendation_letters?access_token=<access_token>"
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
            "updated_at": "2015-07-27T13:23:49-04:00",
            "confidential": false
        },
        {
            "id": 883649378,
            "title": "Recommendation letter from Dr. Smith",
            "filename": "Smith_Recommendation_Letter.docx20150727-138s9s6-1cfz5q0.docx",
            "download_url": "https://chroniclevitae.com/api/documents/883649378/download",
            "updated_at": "2015-07-29T11:14:12-04:00",
            "confidential": true
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
curl -H "Accept: application/vnd.vitae.v2" "https://chroniclevitae.com/api/recommendation_letters/<id>/download?access_token=<access_token>"
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
