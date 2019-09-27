# Tilex - Today I Learned in Elixir

[![CircleCI][ci-image]][ci-url] [![Coverage Status][cov-image]][cov-url]

> Today I Learned is an open-source project by the team at [Hashrocket][hr-url]
> that catalogues the sharing & accumulation of knowledge as it happens
> day-to-day. Posts have a 200-word limit, and posting is open to any Rocketeer
> as well as select friends of the team. We hope you enjoy learning along with
> us.

This site was open-sourced as a window into our development process, as well as
to allow people to experiment with the site on their own and contribute to the
project.

We originally implemented Tilex as [_hr-til_][hr-til-repo], a Ruby on Rails
app.

### Installation

If you are creating your own version of the site, fork the repository.

Then, install Erlang, Elixir, Phoenix, and PostgreSQL.

Next, follow these setup steps:

```shell
$ git clone https://github.com/hashrocket/tilex
$ cd tilex
```

At this point you can use `make` for development commands. To access make help
just type: `make` or `make help`. Then you can run make with target(s) such as:
`make setup server` and so on. Environment variables will automatically loaded
from `.env` file in case you need to change it.

```shell
$ make
$ make setup server
```

Or run commands manually. To set environmental variables, copy the example file:

```shell
$ cp .env{.example,}
```

For setting up the project and start the server manually run:

```shell
$ source .env
$ mix deps.get
$ mix ecto.setup
$ npm install --prefix assets
$ mix phx.server
```

If you'd like to skip the database seeds, run `mix ecto.create && mix
ecto.migrate` in place of `mix ecto.setup`.

Now you can visit localhost:4000 from your browser.

To serve the app at a different port, include the `PORT` environment
variable when starting the server:

```shell
$ PORT=4444 mix phx.server
```

### Authentication

Authentication is managed by Ueberauth and Google. See the [ueberauth_google
README][ueberauth-docs] and [Google Oauth 2 docs][oauth-docs] for setup
instructions. To allow users from a domain and/or comma separated whitelist,
set those configurations in your environment:

```shell
# .env
export GOOGLE_CLIENT_ID="your-key.apps.googleusercontent.com"
export GOOGLE_CLIENT_SECRET="yoursecret"
export HOSTED_DOMAIN="your-domain.com"
export GUEST_AUTHOR_WHITELIST="joedeveloper@otherdomain.com, suziedeveloper@freelancer.com"
```

Once set, visit localhost:4000/admin and log
in with an email address from your permitted domain.

Tilex creates a new user on the first authentication, and then finds that same
user on subsequent authentications.

### Testing

Wallaby relies on [ChromeDriver][chromedriver]; install it via your method of
choice.

Run the tests with:

```shell
$ make test
```

or:

```shell
$ mix test
```

### Deployment

Hashrocket's Tilex is deployed to Heroku. These are Hashrocket's deployed
instances:

- Staging: https://tilex-staging.herokuapp.com
- Production: https://til.hashrocket.com

This project contains Mix tasks to deploy our instances; use as follows:

```shell
$ mix deploy <environment>
```

### Contributing

Please see [CONTRIBUTING][contributing] for more information.

### Code of Conduct

This project is intended to be a safe, welcoming space for collaboration, and
contributors are expected to adhere to the [Contributor Covenant][cc] code of
conduct. Please see [CODE OF CONDUCT][coc] for more information.

### Usage

We love seeing forks of Today I Learned in production! Please consult
[USAGE][usage] for guidelines on appropriate styling and attribution.

### License

Tilex is released under the MIT License. Please see [LICENSE][license] for
more information.

---

### About

[![Hashrocket logo][hr-image]][hr-url]

Tilex is supported by the team at [Hashrocket, a multidisciplinary design and
development consultancy][hr-url]. If you'd like to [work with us][hr-hire-us]
or [join our team][hr-jobs], don't hesitate to get in touch.

[cc]: http://contributor-covenant.org/
[chromedriver]: https://sites.google.com/a/chromium.org/chromedriver/
[ci-image]: https://circleci.com/gh/hashrocket/tilex.svg?style=svg
[ci-url]: https://circleci.com/gh/hashrocket/tilex
[coc]: ./CODE_OF_CONDUCT.md
[contributing]: ./CONTRIBUTING.md
[cov-image]: https://coveralls.io/repos/github/hashrocket/tilex/badge.svg?branch=master
[cov-url]: https://coveralls.io/github/hashrocket/tilex?branch=master
[hr-hire-us]: https://hashrocket.com/contact-us/hire-us/
[hr-image]: https://hashrocket.com/hashrocket_logo.svg
[hr-jobs]: https://hashrocket.com/contact-us/jobs/
[hr-til-repo]: https://github.com/hashrocket/hr-til/
[hr-url]: https://hashrocket.com/
[license]: ./LICENSE.md
[oauth-docs]: https://developers.google.com/identity/protocols/OAuth2WebServer/
[ueberauth-docs]: https://github.com/ueberauth/ueberauth_google
[usage]: ./USAGE.md
