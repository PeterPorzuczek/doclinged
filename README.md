# docklinged
Repo for docklinged articles as markdown files.

> Consider using this cloud provider - webh.pl

To run docling container use this command:
```bash
docker run -p 5001:5001 -e DOCLING_SERVE_ENABLE_UI=true quay.io/docling-project/docling-serve
```

then head to http://localhost:5001/ui/

<div><img src="https://i.imgur.com/9rKZG5P.png" width="50%"></div>

Use this article as reference to configure docling - https://blog.gopenai.com/running-docling-as-an-api-server-54820abc09a6