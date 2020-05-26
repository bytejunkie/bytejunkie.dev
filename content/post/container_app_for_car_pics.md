---
title: "Container App for car pics"
date: 2020-05-18T10:10:36+01:00
draft: false
---

In a life some time ago, before my kids arrived, I loved modified cars. So when I started looking into containers and followed the awesome tutorial at [Docker Curriculum](https://docker-curriculum.com/) I saw an opportunity to rework the Flask app for my own re-use when tinkering with container tutorials and as i worked my way into AWS container functions.

This is the [repo](https://github.com/bytejunkie/carpics) if you want to adjust the app and fork/reuse it.

Its about as basic as it gets. Its a flask app, so a few lines of python, which sets up some dictionaries which link to static content hosted in S3. if you run the app, remember to add "?manufacturer=audi|bmw|vw" to the url or it will error. There are lots of refinements to make to this app, if it were anything other than a quick toy to use when spinning containers up. Maybe some day I'll add to it.

If you wanted to run this app, then it ought to be this simple.

```
git clone https://github.com/bytejunkie/carpics.git
cd carpics
docker build -t <your_repo_name>/carpics .
docker run -p 8080:5000 bytejunkie77/carpics
```

now visit localhost:8080?manufacturer=audi to see some tasty german motors.