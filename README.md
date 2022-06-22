# evg-api-rs

A rust client for the [Evergreen](https://github.com/evergreen-ci/evergreen) REST API.

## Table of contents

- [evg-api-rs](#evg-api-rs)
  - [Table of contents](#table-of-contents)
  - [Description](#description)
  - [Getting Help](#getting-help)
    - [What's the right channel to ask my question?](#whats-the-right-channel-to-ask-my-question)
    - [How can I request a change/report a bug in shrub-rs?](#how-can-i-request-a-changereport-a-bug-in-shrub-rs)
    - [What should I include in my ticket or question?](#what-should-i-include-in-my-ticket-or-question)
  - [Installation](#installation)
  - [Usage](#usage)
    - [Making API calls](#making-api-calls)
    - [More examples](#more-examples)
  - [Contributor's Guide](#contributors-guide)
    - [Setting up a local development environment](#setting-up-a-local-development-environment)
    - [linting/formatting](#lintingformatting)
    - [Running tests](#running-tests)
    - [Versioning](#versioning)
    - [Code Review](#code-review)
    - [Deployment](#deployment)
  - [Resources](#resources)

## Description

A rust library for interacting with the Evergreen REST API.

## Getting Help

### What's the right channel to ask my question?

If you have a question about evg-api-rs, please mention @dag-on-call in slack channel #evergreen-users,
or email us at dev-prod-dag@mongodb.com.

### How can I request a change/report a bug in shrub-rs?

Create a DAG ticket in Jira.

### What should I include in my ticket or question?

Please include as much information as possible. This can help avoid long information-gathering threads.

Please include the following:

- **Motivation for Request**: Why is this change being requested? (This help us understand the priority and urgency of the request)
- **Context**: Is there any background information we should be aware of for this request?
- **Description**: What would you like investigated or changed?

## Installation

To install, include "evg-api-rs" in your projects Cargo.toml dependencies.

## Usage

### Making API calls

A simple example:

```rust
use std::path::Path;
use evg_api_rs::EvgClient;

let evg_auth_file = Path::from("path/to/evergreen.yml");
let evg_client = EvgClient::from_file(&evg_auth_file).expect("Cannot find evergreen auth file")
let task = evg_client.get_task(task_id).unwrap();

println!("Found task: {}", task.display_name);
```

### More examples

For a more complex example of how shrub can be used see the [mongo-task-generator](https://github.com/mongodb/mongo-task-generator).

## Contributor's Guide

### Setting up a local development environment

After cloning the repository, simply run `cargo build` to download and build the project.

### linting/formatting

```bash
cargo fmt
cargo clippy
```

### Running tests

```bash
cargo test
```

### Versioning

This project uses [semver](https://semver.org/) for versioning.

Please include a description what is added for each new version in `CHANGELOG.md`.

### Code Review

Code reviews are required on all changes and are done via Github Pull Requests.

### Deployment

Deployment should be done with the cargo publish command.

## Resources

- [Evergreen REST API](https://github.com/evergreen-ci/evergreen/wiki/REST-V2-Usage)
- [Python API client](https://github.com/evergreen-ci/evergreen.py)
