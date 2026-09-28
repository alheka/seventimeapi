# Errors

<!--
<aside class="notice">
This error section is stored in a separate file in <code>includes/_errors.md</code>. Slate allows you to optionally separate out your docs into many files...just save them to the <code>includes</code> folder and add them to the top of your <code>index.md</code>'s frontmatter. Files are included in the order listed.
</aside>
-->

The Seven Time API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid, e.g. a required field is missing, a parameter has an invalid value, or the 'Content-Type' header is not 'application/json' on a non-GET request.
401 | Unauthorized -- Your API key is wrong, or the user connected to a personal API key is no longer active.
403 | Forbidden -- The API key (or the user connected to a personal API key) does not have permission to access the resource.
404 | Not Found -- The specified resource could not be found.
422 | Unprocessable Entity -- The list query has no filters and could match a very large number of records (`code`: "QUERY_TOO_BROAD"). Add a filter, e.g. a date range.
429 | Too Many Requests -- The rate limit has been exceeded. See 'Rate-limit'.
500 | Internal Server Error -- We had a problem with our server. Note that many validation errors that occur when creating or updating a resource are also returned with HTTP 500 and a descriptive `errorMessage`.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

When applicable the error message will be available in the response as `errorMessage`. 
