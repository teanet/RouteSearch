# Route search
Example
`SCHEME://2gis.ru/REGION_CODE/routeSearch/rsType/ROUTING_TYPE/from/lon,lat╎FROM_DISPLAY_NAME╎FROM_OBJECT_ID╎geo/to/lon,lat╎TO_DISPLAY_NAME╎TO_OBJECT_ID╎geo`

`SCHEME`, required – `https` or `dgis`
`REGION_CODE`, optional – region internal code of region ex. `novosibirsk`, `omsk`
`ROUTING_TYPE`, optional – routing type ex. `car`, `bus` (default `bus`)
`lon,lat`, required – longitude and latitude of route point ex. `82.898712,55.073257`
`FROM_DISPLAY_NAME`, `TO_DISPLAY_NAME`, optional – display name of route point, if not present use `lon,lat` as description
`FROM_OBJECT_ID`, `TO_OBJECT_ID`, optional – internal id of desired point, can be found at 2gis.ru  

Olso you can use `my_location` as route point ex.
`https://2gis.ru/routeSearch/from/my_location/to/82.898712,55.073257`

If there is no from or to point exists, we use `my_location` for missing point ex.
`https://2gis.ru/routeSearch/to/82.898712,55.073257` will be treated as
`https://2gis.ru/routeSearch/from/my_location/to/82.898712,55.073257`
and
`https://2gis.ru/routeSearch/from/82.898712,55.073257` will be treated as
`https://2gis.ru/routeSearch/from/82.898712,55.073257/to/my_location`

We can only build route if both route points will be located in the same region.
If you don't provide region code, we try to parse both route points, and, if threy are both in the same region we show that region, if possible, and build route
