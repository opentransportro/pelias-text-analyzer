> This repository is part of the [Pelias](https://github.com/pelias/pelias) project. Pelias is an open-source, open-data geocoder originally built by [Mapzen](https://www.mapzen.com/). Our official user documentation is [here](https://github.com/pelias/documentation).

# Pelias Text Analyzer

## Overview

Module that performs analysis of a single line of input describing a location, breaking into its constituent parts (street, city, state, country, etc).

**Note: this module has been merged back into [pelias/api](https://github.com/pelias/api) and is now deprecated**

## Installation

To use the libpostal address parser, libpostal must be [installed](https://github.com/openvenues/libpostal/blob/master/README.md#installation) locally.

```bash
$ npm install pelias-text-analyzer
```

#### About

This package is responsible for textually analyzing a single line input into it's constituent parts.  That is, the input `30 West 26th Street, New York, NY 10010` is parsed into:

```
{
  number: '30',
  street: 'west 26th street',
  city: 'new york',
  state: 'ny',
  postalcode: '10010',
  country: 'usa'
}
```

The point of this module isn't to hardwire Pelias to a certain text analyzer but to provide an interface for future work.

#### Supported Parsers

Currently, there are 2 supported parsers:

- [AddressIt](https://www.npmjs.com/package/addressit)
- [libpostal](https://github.com/openvenues/libpostal) via [node-postal](https://github.com/openvenues/node-postal)

As libpostal support increases, AddressIt support will be shelved.

#### Configuration

Selection of AddressIt or libpostal is made using the Pelias configuration value found in `api.textAnalyzer`, defaulting to `addressit` if not found.  For example, this will use libpostal for text analysis in the text-analyzer project:

```
{
  "api": {
    "textAnalyzer": "libpostal"
  }
}
```
