## Introduction

    This is an implementation of a URL Shortener Implementation without use of any external API using SHA1 encryption.

    The long URL which will be given to us will be in the format of
    https://localhost:5050/track-link/A-23-Depot-Z-M-01?id=${uuid}"

    uuid is unique identifier of 36 characters

## Problem Statement
    The problem statement is to convert this long url into a shortened url. Whenever we click on this shortened url, it should redirect us to the long url and eventually to the webpage that the long url is directing to.

## Implementation
    The original url is encrypted using SHA-1 to a 40 hex encrypted hash.

    We slice this 40 hex hash into 5 equal parts of 8 hex each, which is converted into decimal which again is base62 encoded.

    This splitting into 5 equal parts is done to make sure that our final base-62 encrypted string will have a length of ≤ 7, since the main target is to produce a shortened url.

    This shortened url is then stored in database along with the original long url as a kind of a mapper, which will be used while redirection of the shortened url to the original url.

    Now while storing the shortened url in database, we will first check if this shortened url exists or not. If it exists, then we will put some degree of randomness and will generate the shortened url again.

## Test Results
    One can run test/url-shorten.js file to see the working of shortener

    Repeats in a run of 1000000 are 99 with repeat percentage of 0.009899999999999999.

    Repeats in a run of 8500000 are 8416 with repeat percentage of 0.09901176470588235.

    Repeats in a run of 10000000 are 11725 with repeat percentage of 0.11725.