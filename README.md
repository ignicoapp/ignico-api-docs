# Ignico API Documentation

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/9840d195c6a5a3e0e32c)

Ignico is **rewards & commission automation engine** that helps businesses create their referral, loyalty, MLM, gamification or social selling program on the top of existing e-commerce platforms or CRM's [(read more about Ignico)](http://igni.co/).

You can read API Documentation by visiting http://api.igni.co

---

Each Ignico instance exposes API for developers to consume in their applications.

The API allows you to automate some tasks you typically would do through Ignico web app interface like:
- batch import of your data to your app,
- get your calculation results, user actions, rewards etc.

You can check here what resources you can interact with and how your requests should look like.



## Authorization

If you are a customer and have your own Ignico workspace set, you or one of your administrators have to create an API Key first.

To access any endpoint (except fetching access token) you have to be authorized. We use [The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749) to grant you access.



## Conventions

All communication is done in REST way and JSON format is used for each request and response.

Every endpoint conforms to open source JSON API 1.0 Specification. You can find everything you need to know about this format in official docs on http://jsonapi.org.



## Filtering

JSON API does not impose filtering params format (http://jsonapi.org/format/#fetching-filtering) so we chose to use it in array like notation.

To use a filter `someFilter` you need to send it as `filter[someFilter]=someValue` query parameter.

Of course you can combine multiple filters like this:

`?filter[someFilter]=someValue&filter[otherFilter]=otherValue`



## Pagination

JSON API is agnostic about pagination strategy (http://jsonapi.org/format/#fetching-pagination) too so we chose to use page-based strategy.

By default you will fetch first page and first 25 records (other default page size can be specified by endpoints). You can get information about total records count, current page or current page size from `meta` (http://jsonapi.org/format/#document-meta) information.

To fetch other pages or more data you need to send it as `page[number]=2&page[size]=10` query parameters.

Maximum page size may be limited and can be specified by endpoints to prevent sending too much data over single request.
