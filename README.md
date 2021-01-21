

# Content segmentation with InfoListProvider

### Description

Complex content segmentation needs in Liferay DXP 7.2 can be solved by using InfoListProvider.

Basically, you just have to create an implementation of InfoListProvider, declare the type of the contents in your list, and return the desired list of contents using your own strategy of query.

Here is a real world scenario of content segmentation:

-   General objective: Find the banner to be displayed in the principal portal page

-   Rules:

1. Find the most recent JournalArticle. At least one of its tags must match with at least one of the tags of the user.
2. If there is no JournalArticle in the filter above, so find the most recent JournalArticle set by public for everyone.
3. Only JournalArticles that have been published in the last 48 hours.

I’ve used ElasticSearch queries instead of conventional SQL for better performance.

### Setup a demo

1. Create a category `segmentation`
1. Create some content items and each content item must have the `segmentation` category
1. Each content item should also have a tag, e.g. `sales` or `marketing` or `hr`.
1. In the profile of each user you must define one of the tagnames you used
1. Now you can use the Principal Banner to select content


### Sources
[https://github.com/marceltanuri/content-segmentation-with-info-list-provider](https://github.com/marceltanuri/content-segmentation-with-info-list-provider)
[dev/24](https://youtu.be/K6uDFo8kilI?t=17827)

References:

-   [https://help.liferay.com/hc/en-us/articles/360029067271-Creating-an-Information-List-Provider](https://help.liferay.com/hc/en-us/articles/360029067271-Creating-an-Information-List-Provider)
    
-   [https://help.liferay.com/hc/en-us/articles/360029046391-Search-Queries-and-Filters](https://help.liferay.com/hc/en-us/articles/360029046391-Search-Queries-and-Filters)
    
-   [https://help.liferay.com/hc/en-us/articles/360029046411-Building-Search-Queries-and-Filters](https://help.liferay.com/hc/en-us/articles/360029046411-Building-Search-Queries-and-Filters)
    
-   [https://github.com/liferay/liferay-portal/tree/7.2.x/modules/apps/portal-search/portal-search-api/src/main/java/com/liferay/portal/search/query](https://github.com/liferay/liferay-portal/tree/7.2.x/modules/apps/portal-search/portal-search-api/src/main/java/com/liferay/portal/search/query)
