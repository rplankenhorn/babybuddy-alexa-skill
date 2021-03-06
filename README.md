# babybuddy-alexa-skill

## Introduction

This is an Alexa skill to help supplement the [Baby Buddy](https://github.com/babybuddy/babybuddy) server and allow users to record diaper changes, feedings, tummy times, etc. with their voice.

### Minimum Baby Buddy version

This skill requires Baby Buddy v1.4.1 or newer as it relies on Baby Buddy's API allowing null values for the `Timer.user` field.

## Usage

For actions that require a duration, a start keyword creates a named timer and a stop keyword closes out that timer and creates the feeding, tummy time, sleep, etc.

Currently, all intents allow you to specify which child but if no child is specified and there is only one child in the system, it will assume that child.  TODO:  If there is more than one child and no child is specified, prompt user for which child.

There are a lot of ways to instantiate any given intent and they can be found by examining the [interaction model](https://github.com/babybuddy/babybuddy-alexa-skill/blob/master/skill-package/interactionModels/custom/en-US.json).

### Feedings

```
Alexa, ask Baby Buddy to start feeding (for [Child's Name])
Alexa, ask Baby Buddy to stop feeding (for [Child's Name])
```

### Tummy Time

```
Alexa, ask Baby Buddy to start tummy time (for [Child's Name])
Alexa, ask Baby Buddy to stop tummy time (for [Child's Name])
```

### Sleeping

```
Alexa, ask Baby Buddy to start sleeping (for [Child's Name])
Alexa, ask Baby Buddy to stop sleeping (for [Child's Name])
```

### Diaper Change

```
Alexa, ask Baby Buddy to log diaper change (for [Child's Name])
```

### Last Feeding

```
Alexa, ask Baby Buddy when was the last feeding (for [Child's Name])
```

## Dependencies

### Yarn

This project uses [yarn](https://yarnpkg.com/getting-started/install) for dependency management.

### ASK CLI

This project depends on the [ask-cli](https://github.com/alexa/ask-cli) for deployment to AWS.  Please follow the instructions [here](https://github.com/alexa/ask-cli) to install.

Note:  The ask-cli cannot be installed using yarn and has to be installed using npm.

## Deployment

### 1. Create ```skill.json```, ```ask-resources.json```, and ```ask-states.json```

```
cd lambda/custom
yarn
yarn setup # Will prompt for Baby Buddy URL and API key
```

### 2. Deploy

The ask-cli deploy command will automatically create the skill on your AWS account and a lambda function.  This needs to be done first in order to get local development to work.

```
ask deploy
```

## Local Development

The setup script will create a VSCode launch.json file to use for local development.  Developers can use something like [ngrok](https://ngrok.com/download) to redirect requests to their local dev instance for debugging.  Just update the Endpoint section on the Build tab at [developer.amazon.com](https://developer.amazon.com) to use the ngrok URL.
