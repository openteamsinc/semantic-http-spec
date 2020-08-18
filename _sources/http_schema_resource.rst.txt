.. index:: HTTP Schema Resource

.. _HTTP Schema Resource:

********************
HTTP Schema Resource
********************

An *HTTP Schema Resource* is a JSON resource providing a detailed description
of the HTTP methods supported by an HTTP resource and is intended to be
provided as the entity body on a successful response of the HTTP OPTIONS
method.

An :ref:`HTTP Schema Resource` is an OpenAPI [openapi]_ Operations object.  The
definition of :ref:`HTTP Schema Resource` extends the definition of OpenAPI
Media Type such that Media Type objects **MUST** provide a ``schema`` property
and a ``context`` property. The value of a Media Type ``schema`` property
**MUST** be the URI of a schema defining valid content for the Media Type. The
value of a Media Type ``context`` property **MUST** be the URI of an RDF
context resource for the Media Type.

Example
=======

.. sourcecode:: json

   {
      "get": {
         "responses": {
            "200": {
                "description": "OK"
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url>"
                        , "schema": "<json-schema url>"
                    }
                }
            }
         }
      }
      , "put": {
         "requestBody": {
            "description": "The updated content for the resource."
            , "required": true
            , "content": {
                "application/json": {
                    "context": "<json-ld context url>"
                    , "schema": "<json-schema url>"
                }
            }
         }
         , "responses": {
            "200": {
                "description": "OK"
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url>"
                        , "schema": "<json-schema url>"
                    }
                }
            }
            , "400": {
                "description": "BAD REQUEST: The request was malformed or
                                missing required content."
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url for error objects>"
                        , "schema": "<json-schema url for error objects>"
                    }
                }
            }
            , "401": {
                "description": "UNAUTHORIZED: The request requires
                                authentication."
            }
            , "403": {
                "description": "FORBIDDEN: The requires requires
                                permissions the current authenticated
                                request does not have."
            }
         }
      }
      , "delete": {
         "responses": {
            "200": {
                "description": "OK"
            }
            , "400": {
                "description": "BAD REQUEST: The request was malformed or
                                missing required content."
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url for error objects>"
                        , "schema": "<json-schema url for error objects>"
                    }
                }
            }
            , "401": {
                "description": "UNAUTHORIZED: The request requires
                                authentication."
            }
            , "403": {
                "description": "FORBIDDEN: The requires requires permissions
                                the current authenticated request does not
                                have."
            }

         }
      }
   }

JSON Schema
===========

..
  jsonschema:: ./http_schema_json_schema.json

.. literalinclude:: http_schema_json_schema.json
   :language: json

JSON-LD Context
===============

.. literalinclude:: http_schema_json_ld.json
   :language: json

HTTP Examples
=============

OPTIONS
-------

Request
^^^^^^^

.. sourcecode:: http

   OPTIONS /api/person/foo HTTP/1.1
   Host: example.com
   Accept: application/json
   Authorization: Basic V2h5IGFyZSB5b3UgbG9va2luZyBhdCB0aGlzPyBJdCdzIGEgc2VjcmV0IQ==

Response
^^^^^^^^

.. sourcecode:: http

   HTTP/1.1 200 OK
   Date: Thu, 04 Apr 2019 15:15:15 GMT
   Content-Length: XXXXX
   Content-Type: application/json
   Last-Modified: Mon, 20 Jul 2015 14:15:15 GMT
   ETag: "XXXX"
   Link: <http://scrud.io/schemas/semantic_http.json>; rel=”describedby”
   Link: <https://scrud.io/contexts/semantic_http.json>;
         rel="http://www.w3.org/ns/json-ld#context";
         type="application/ld+json"

   {
      "get": {
         "responses": {
            "200": {
                "description": "OK"
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url>"
                        , "schema": "<json-schema url>"
                    }
                }
            }
         }
      }
      , "put": {
         "requestBody": {
            "description": "The updated content for the resource."
            , "required": true
            , "content": {
                "application/json": {
                    "context": "<json-ld context url>"
                    , "schema": "<json-schema url>"
                }
            }
         }
         , "responses": {
            "200": {
                "description": "OK"
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url>"
                        , "schema": "<json-schema url>"
                    }
                }
            }
            , "400": {
                "description": "BAD REQUEST: The request was malformed or
                                missing required content."
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url for error objects>"
                        , "schema": "<json-schema url for error objects>"
                    }
                }
            }
            , "401": {
                "description": "UNAUTHORIZED: The request requires
                                authentication."
            }
            , "403": {
                "description": "FORBIDDEN: The requires requires
                                permissions the current authenticated
                                request does not have."
            }
         }
      }
      , "delete": {
         "responses": {
            "200": {
                "description": "OK"
            }
            , "400": {
                "description": "BAD REQUEST: The request was malformed or
                                missing required content."
                , "content": {
                    "application/json": {
                        "context": "<json-ld context url for error objects>"
                        , "schema": "<json-schema url for error objects>"
                    }
                }
            }
            , "401": {
                "description": "UNAUTHORIZED: The request requires
                                authentication."
            }
            , "403": {
                "description": "FORBIDDEN: The requires requires permissions
                                the current authenticated request does not
                                have."
            }

         }
      }
   }

