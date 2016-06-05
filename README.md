# elm-jsonapi

elm-jsonapi decodes any JSON API compliant payload and provides helper functions for working with the results.

```
import Http
import JsonApi exposing (primaryResource)
import JsonApi.Decode exposing (document)
import Task exposing (..)


getUserResource : String -> Task Http.Error (JsonApi.Document)
getUserResource query =
    Http.get document ("http://www.jsonapi-compliant-server.com/users/" ++ query)

extractUsername : JsonApi.Document -> Maybe String
extractUsername doc =
  primaryResource doc
    |> Result.toMaybe
    |> Maybe.map JsonApi.attributes
    `Maybe.andThen` (Dict.get "username")
```

## contributing

elm-jsonapi is currently under development. I use waffle.io and Github Issues to track new features and bugs. if there's a feature you'd like to see, please
[submit an issue](https://github.com/noahzgordon/elm-jsonapi/issues/new)! 

if you'd like to contribute yourself, please reach out to me or submit a pull request for the relevant issue.

[![Stories in Ready](https://badge.waffle.io/noahzgordon/elm-jsonapi.png?label=ready&title=Ready)](http://waffle.io/noahzgordon/elm-jsonapi)