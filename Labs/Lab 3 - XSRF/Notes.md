# Cross-Site Request Forgery Attack Lab

## Motivation

Since our project will involve a similar attack to this (CSRF), we have decided to use this Seed Labs as preparation and research.

## Task 1: Observing HTTP Request

Inspecionando os requests HTTP quando o `seed-server.com` é iniciado através do add-on HTTP Header Live, conseguimos observar dois:

- Request GET

```note

```

- Request POST

```note
Host: www.seed-server.com
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:83.0) Gecko/20100101 Firefox/83.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
X-Elgg-Ajax-API: 2
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------139382037620708817074255733343
Content-Length: 695
Origin: http://www.seed-server.com
Connection: keep-alive
Referer: http://www.seed-server.com/
Cookie: Elgg=uaeqppra1jjncbjcjii6c3685p
```

## Task 2: CSRF Attack using GET Request



## Task 3: CSRF Attack using POST Request



## Task 4: Enabling Elgg’s Countermeasure



## Members

- Fabio Sá (up202007658@up.pt)
- Inês Gaspar (up202007210@up.pt)