# reproduce-a-stack-trace

## Create a GitHub repository

It has to be public.

## Set up Travis

I didn't have a [Travis](https://travis-ci.org/) account. Creating one is easy
if you already have a Github account: just visit the Travis site and click
"Sign in with GitHub". You'll have to approve some permissions Travis needs,
but they are reasonable.

Go to [your profile page](https://travis-ci.org/profile/) and select the
organization (or yourself) where you created the repository. Then find the
repository listed and click it to turn on Travis builds for it.

## Simple stack trace

https://samebug.io/exceptions/173939/java.lang.IndexOutOfBoundsException/index-256-size-256

## Initialise project

Create a simple project structure running
```
gradle init --type java-library
```

It will create a minimal java project. All you have to do is change
`src/main/java/Library.java` to contain your code that throws the exception you
want.
