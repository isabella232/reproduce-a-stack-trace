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

Original: https://samebug.io/exceptions/173939/java.lang.IndexOutOfBoundsException/index-256-size-256
Reproduced: https://travis-ci.org/samebug/reproduce-a-stack-trace/builds/327664326#L485-L489

## Initialise project

Create a simple project structure running
```
gradle init --type java-library
```

It will create a minimal java project. All you have to do is change
`src/main/java/Library.java` to contain your code that throws the exception you
want.

Edit your `build.gradle` file to include this snippet. It will make gradle
print the full stack trace on the console. By default, it prints only a short
form of the stack trace and the full report is available in a separate file
which is difficult to access on the Travis server.
```
test {
    testLogging {
        events "failed"
        exceptionFormat "full"
    }
}
```

## Get the link to the stack trace

Visit your failed build at Travis. Scroll down to the stack trace, click on its
first row, then holding down the shift key click on its last row. The link in
the browser will change to include an anchor of the form
`#L<first-line-number>-L<last-line-number>`.
