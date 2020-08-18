************
Introduction
************

The combination of HTTP and HTML are the foundation of the web. The success of
this combination starts with the standardization of these two elements and
later resource formats. The implied default rendering of HTML for viewing and
the inclusion of hyperlinks in HTML resources for discovery and rendering of
additional resources strengthened that standard and led to the network effects
that resulted in the web we have today.

This specification builds upon the original web standards by defining a
standard set of hyperlinks and entity resource types to provide a rich
description of both the data provided by an HTTP API and the HTTP methods
supported for every resource provided by that API. The intent of this
specification is to enable RESTful APIs to provide enough typing and semantic
data to allow a browsing application to render a meaningful and complete user
interface for that API, much as a browser can render an HTML resource.

While a default rendering is valuable and necessary, it's not enough for a
truly rich user interface and user experience. Much like stylesheets and
JavaScript were added to HTML to provide a richer user-experience, this
standard sets a foundation for richer user-interfaces informed by the RDF
semantic types associated with data in a RESTful API to provide a basis for
stylized renderings based upon the semantic meaning of the data and the display
context. For example, knowing that a JSON object has a set of string properties
can inform a crude display of those propserties, having the knowledge that the
object is an address with street, city, state, and zip code properties can
enable the rendering browser the opportunity to instead render a map zoomed in
to that address with a pin marking the location of that address.

Merely rendering the resources that support GET in a rich way is insufficient
as well. Resource URLs that support POST or PUT should be similarly supported
for resources that may be created or edited. This specification provides a
mechanism for a browsing application to discover both the schema for
well-formed API requests as well as the semantic meaning of valid request data
to better inform rich editor rendering of that data.

This specification defines the requirements for RESTful Semantic HTTP APIs.
There are three requirements: a schema header, an RDF context header, and
a specific implementation of the HTTP OPTIONS method.

