# Avanti Search

## Install

1. `$ bower install avanti-search --save`.
2. Install [JS-Cookie](https://github.com/js-cookie/js-cookie).
3. Insert `avanti-search.js` in your store.
4. Insert `avanti-search.css` in your store.
5. Insert VTEX search result tag `<vtex.cmc:searchResult/>` in your template.
6. Insert below script in your template at the bottom. Inside `<body>` tag:
```html
<script>
    var scriptContent = $('.resultItemsWrapper').children('script').html();
    eval('window.'+ /(PageClick_)([0-9]+)/g.exec(scriptContent)[0] +' = function () {}');
</script>
```
7. Call plugin in your JavaScript:
```javascript
(function() {
    $('.resultItemsWrapper div[id^="ResultItems"]').avantiSearch();
})();
```

## Options

##### Elements

| Option | Type | Default | Description |
|--- |--- |--- |--- |
| $resultItemsWrapper | Element | `$('.resultItemsWrapper')` | Description |
| $script | Element | `$('.resultItemsWrapper').children('script')` | Description |
| $totalItems | Element | `$('.searchResultsTime:first .resultado-busca-numero .value')` | Description |
| $selectOrder | Element | `$('#O')` | Description |
| $filters | Element | `$('.search-multiple-navigator label')` | Description |

##### Classes

| Option | Type | Default | Description |
|--- |--- |--- |--- |
| classFilterActive | String | `filter--active` | Description |
| classItemPreLoad | String | `shelf-item--preload` | Description |
| classLoadBtnHide | String | `load-btn--hide` | Description |
| classLoadLess | String | `load-less` | Description |
| classLoadMore | String | `load-more` | Description |
| classPagination | String | `pagination` | Description |

##### Texts

| Option | Type | Default | Description |
|--- |--- |--- |--- |
| textLoadLess | String | `Load less` | Description |
| textLoadMore | String | `Load more` | Description |
| textPaginationFirst | String | `First` | Description |
| textPaginationPrev | String | `Prev` | Description |
| textPaginationNext | String | `Next` | Description |
| textPaginationLast | String | `Last` | Description |
| textEmptyResult | String | `No product found` | Description |

##### Pagination

| Option | Type | Default | Description |
|--- |--- |--- |--- |
| pagination | Boolean | `false` | Description |
| paginationRangeButtons | Number | `3` | Description |

##### Others

| Option | Type | Default | Description |
|--- |--- |--- |--- |
| cookieName | String | `AvantiSearchQuery` | Description |
| defaultParams | Object | `{}` | Pass default params to request.<br>**Example:** `{ 'query': { 'O': 'OrderByPriceASC' } }` |
| attempts | Number | `1` | Description |

**Example:**

```javascript
(function() {
    $('.resultItemsWrapper div[id^="ResultItems"]').avantiSearch({
        cookieName: 'AvantiSearchQuery',
        defaultParams: {
            'query': {
                'O': 'OrderByPriceASC'
            }
        }
    });
})();
```

## Events

| Event name | Arguments | Description |
|--- |--- |--- |
| avantisearch.init | event, options, request | Description |
| avantisearch.initWithCookie | event, options, request | Description |
| avantisearch.beforeSearch | event, options, request | Description |
| avantisearch.afterSearch | event, options, request | Description |
| avantisearch.beforeChangeOrder | event, options, request, element | Description |
| avantisearch.afterChangeOrder | event, options, request, element | Description |
| avantisearch.beforeFilter | event, options, request, element | Description |
| avantisearch.afterFilter | event, options, request, element | Description |
| avantisearch.beforeChangePage | event, options, request | Description |
| avantisearch.afterChangePage | event, options, request | Description |
| avantisearch.beforeShowItems | event, options, request, page | Description |
| avantisearch.afterShowItems | event, options, request, page | Description |

**Example:**
```javascript
(function() {
    var $resultItems = $('.resultItemsWrapper div[id^="ResultItems"]');

    $resultItems
        .on('avantisearch.init', function (event, options, request) {
            console.log(event);
            console.log(options);
            console.log(request);
        });

    $resultItems.avantiSearch();
})();
```

## Tips and Tricks

1. Call the events: `avantisearch.init` or `avantisearch.beforeSearch` before the plugin start.

## Dependencies

- [JS Cookie](https://github.com/js-cookie/js-cookie)

## Contributing

- [CONTRIBUTING.md](CONTRIBUTING.md)
