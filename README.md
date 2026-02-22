# Portfolio Website

This is my personal portfolio website. It is built using Jekyll (Ruby) and was initially based off of rosario's [Kasper](https://github.com/rosario/kasper.git) Jekyll theme. Since then, it has gone through a number of changes. It's current state utilizes the [tacit](https://github.com/yegor256/tacit) CSS framework. The website is hosted directly on GitHub utilizing GitHub Pages - an action automatically deploys on every merge to main.

## Local Development

### Prerequisites

- [Ruby](https://www.ruby-lang.org/en/documentation/installation/)
- [Jekyll](https://jekyllrb.com/docs/installation/)

### Running locally

```bash
jekyll serve
```

The site will be available at `http://localhost:4444`.

To access the site from other devices on the same network:

```bash
jekyll serve --host 0.0.0.0
```

Then visit `http://<your-local-ip>:4444` from the other device.