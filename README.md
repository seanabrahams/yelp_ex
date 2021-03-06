# YelpEx

An Elixir client for the Yelp Fusion API (aka *Yelp's API v3*).

See the Yelp API docs
[here](https://www.yelp.com/developers/documentation/v3/).

See the [Hex documentation](https://hex.pm/packages/yelp_ex)
for more information.


## Installation

Add `:yelp_ex` to your `mix.exs` file as a dependency and to
your `extra_applications` list:

```elixir
def application do
  [extra_applications: [:logger, :yelp_ex]]
end

defp deps do
  [{:yelp_ex, "~> 0.2.0"}]
end
```

*Important:* You must use `YelpEx` version 0.2.0 or higher due
to a change in how the Yelp Fusion API authenticates.

Then, run: `mix do deps.get, compile`


## Yelp Setup

In order to use `YelpEx`, you need to create an application on
[Yelp's developer website](https://www.yelp.com/developers/v3/manage_app).
After you do this, you will get an "App ID" and an "App Secret".

Yelp uses an *API key* to authenticate.

Before starting your application, you will need to save your
Yelp API key as an **environment variable**...

One way to do this is to create a file called `.env` in your
project root with the following:

```bash
export YELP_API_KEY="<YOUR_YELP_API_KEY>"
```

Execute the file from the command line:

```bash
$ source .env
```

_**When you start your application, an authenticated, supervised
`YelpEx.Client` will also be started.**_

```bash
$ iex -S mix
```


## Usage
_Click endpoint links to see all valid parameters that can be
passed in `options`._

#### [/businesses/search](https://www.yelp.com/developers/documentation/v3/business_search) Endpoint

```elixir
iex> options = [params: [sort_by: "distance", longitude: -75.145101, latitude: 39.54364]]
[params: [sort_by: "distance", longitude: -75.145101, latitude: 39.54364]]

iex> YelpEx.Client.search(options)
{:ok, {<RESPONSE>}}

iex> YelpEx.Client.search!(options)
{<RESPONSE>}
```

#### [/businesses/search/phone](https://www.yelp.com/developers/documentation/v3/business_search_phone) Endpoint

```elixir
iex> options = [params: [phone: "+14159083801"]]

iex> YelpEx.Client.search_phone(options)
{:ok, {<RESPONSE>}}

iex> YelpEx.Client.search_phone!(options)
{<RESPONSE>}
```
