.. index:: Semantic JSON APIs

.. _Semantic JSON APIs:

******************
Semantic JSON APIs
******************

A RESTful JSON API that conforms to this specification:

  **MUST** provide the schema link header specifying the url of the json-schema
  for the resource.

  .. sourcecode:: http

     Link: <http://example.com/schemas/user.json#>; rel=”describedby”

  **MUST** provide the RDF context link header specifying the JSON-LD context
  for the resource.

  .. sourcecode:: http

     Link: <https://json-ld.org/contexts/person.jsonld>;
     rel="http://www.w3.org/ns/json-ld#context"; type="application/ld+json"

  **MUST** implement OPTIONS and provide the :ref:`HTTP Schema Resource` as the
  entity response detailing the HTTP methods supported by the resource along
  with the schema and context links for the request and response entity bodies.
