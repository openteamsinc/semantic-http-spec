.. index:: Schema Link Header

.. _Schema Link Header:

******************
Schema Link Header
******************

A conforming :ref:`Semantic HTTP Resource` **MUST** provide a ``link`` header
for any HTTP response that returns an entity body specifying a schema resource.
The ``link`` header **MUST** include a ``rel`` attribute with the value of
``describedBy`` or recognized equivalent. There is no recognized equivalent
value for the ``rel`` attribute in this revision of the standard.

Example
=======

An XML resource format may be defined or described by an XML schema. A *Schema
Link Header* for the XML schema would look like:

.. sourcecode:: http

   link: <http://example.com/schemas/user.xml>;
         rel="describedBy";
         type="application/xml"

