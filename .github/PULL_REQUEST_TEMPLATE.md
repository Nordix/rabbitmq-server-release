## Proposed Changes

Adds a GitHub Actions workflow that triggers on published releases and produces a RabbitMQ server source archive, then uploads it to Artifactory.

Adds Vex report generation

What it does
Installs Erlang/Elixir and build dependencies via apt

Runs make source-dist to produce a tar.xz source archive

Uploads the archive to Artifactory under allies-erlang/rabbitmq-server//

Nordix fork handling
This release targets Nordix forks of four upstream RabbitMQ components. The workflow derives the correct refs automatically from the release tag (e.g. v3.8.9-est-1):

UPSTREAM_TAG (v3.8.9) — used for current_rmq_ref/base_rmq_ref so all standard upstream deps resolve to the correct tag

NORDIX_BRANCH (v3.8.9-est) — used for the four Nordix fork overrides:

rabbitmq-server (Nordix)

rabbitmq-management (Nordix)

rabbitmq-federation-management (Nordix)

rabbitmq-amqp1.0-common (Nordix)

The three named Nordix dep overrides are defined in rabbitmq-components.mk via NORDIX_RELEASE_TAG. dep_amqp10_common is exported as an environment variable so it is inherited by all sub-makes during the build.


## Types of Changes

What types of changes does your code introduce to this project?
_Put an `x` in the boxes that apply_

- [x] Bug fix (non-breaking change which fixes issue #NNNN)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause an observable behavior change in existing systems)
- [ ] Documentation improvements (corrections, new content, etc)
- [ ] Cosmetic change (whitespace, formatting, etc)

## Checklist

_Put an `x` in the boxes that apply. You can also fill these out after creating
the PR. If you're unsure about any of them, don't hesitate to ask on the
mailing list. We're here to help! This is simply a reminder of what we are
going to look for before merging your code._

- [x] I have read the `CONTRIBUTING.md` document
- [ ] I have signed the CA (see https://cla.pivotal.io/sign/rabbitmq)
- [x] All tests pass locally with my changes
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] I have added necessary documentation (if appropriate)
- [x] Any dependent changes have been merged and published in related repositories

## Further Comments

If this is a relatively large or complex change, kick off the discussion by
explaining why you chose the solution you did and what alternatives you
considered, etc.
