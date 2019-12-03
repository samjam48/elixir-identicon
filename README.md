# Identicon Generator

## About

This app creates a unique identicon based on an input string.

Users can have a unique identicon made for them if they do not upload a profile image (as seen on sites like github).

The identicon generator always creates the same identicon based on the same string. So images can be created on the fly and do not need to be stored.

##### Example

The _Identicon_ generated for my name _"Sam"_ is:

![Sam Identicon](/identicons/Sam.png)

## How

An identicon is a square 300x300px image made of 25 smaller squares on a 5x5 grid that is mirrored down the middle.

![Identicon grid](/assets/identicon_grid.png)

##### Create a Hex

Each string passed to the function is turned into an MD5 hash and returned as an array of 16 numbers.

##### Pick a Color

The first three numbers in the array are used to define the RGD color value.

##### Generate grid

The first 15 numbers are used to determine true or false on whether a square will have colour in it for the first three columns in the square. We make five arrays of three numbers.

_(we throw away the sixteenth number)_

Mirror first two number of each array to turn it into a 5 number array that is the whole row.

##### Draw image

We make a pixel map with on a 300x300 px map and draw to an image

---

## Running Locally

Install Erlang and Elixir - [Instructions](https://elixir-lang.org/install.html)

Open Elixir shell - `>> iex -S mix`

Run main Identicon function with your desired string

```
iex> Identicon.main("my_string_here")
```

Identicons are generated and added to the `'/identicons'` folder as a png.

---

## Install and use as a Package

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `identicon` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:identicon, "~> 0.1.0"}
  ]
end
```

Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at [https://hexdocs.pm/identicon](https://hexdocs.pm/identicon).

---

Thanks to Stephen Grider and his tutorial on Elixir and identicon creation!
