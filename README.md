# kaushalya.github.io

Personal page built with [Indigo Minimalist Jekyll template](http://sergiokopplin.github.io/indigo/).

## Prerequisites

- Ruby (see `.ruby-version` for recommended version)
- Bundler
- Ruby Development Kit (e.g., `ruby-dev` on Debian/Ubuntu)

## Getting Started

1.  **Install Dependencies:**

    ```bash
    bundle install
    ```

2.  **Build the Site:**

    To build the static site files into the `_site` directory:

    ```bash
    bundle exec jekyll build
    ```

    Alternatively, you can use the Rake task defined in the project:

    ```bash
    rake site
    ```

3.  **Run Locally:**

    To build the site and serve it on a local development server:

    ```bash
    bundle exec jekyll serve
    ```

    The site will be available at `http://localhost:4000` by default. The server will automatically watch for changes and regenerate the site.

## Troubleshooting

### Bundler Permission Error

If you encounter a `Bundler::PermissionError` when running `bundle install`, it means you don't have permission to write to the system's gem directory.

To fix this, configure Bundler to install gems locally within the project:

```bash
bundle config set --local path 'vendor/bundle'
```

Then, run `bundle install` again.
