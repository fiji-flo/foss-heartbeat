# Preliminary Road Map

Where to go from here. And how much effort will it be.

## Current Limitations

- tedious processing
  * lots of commands to execute
  * arguments are confusing
- not able to process big repositories
  * CoreNLP run OOM
- not able to to just update a repository
- continuous scraping and updating (monitoring) missing
- out of the box plotly looks nice but has some navigation / rendering issues
- lacking robustness
  * missing data like no issue in a given time frame can cause crashes
  * hard coded *templating*

## Quick Wins / Dirty Hacks

### Basic Automation

Somehow automating the process for a repository would be the biggest win. This
can be achieved with a simple script (making some assumptions).

Something like:
```bash
$ ./scrape_and_analyse.sh mozilla/mozillians
```
could replace all the manual steps.

### Supporting larger Repositories

A brief look into the [CoreNLP] source code, gave the impression that by simply
chunking the comments and use `-fileList` instead of `-file` we can solve this
issue. This needs some minor adjustments in the python code, though.

## Here be Dragons (looking far far ahead)

We could provide a service version of **foss-heartbeat** that monitors
repositories and provides badges like [Travis CI]. This could indicate the status
of the project and link to more detailed report.

### How to get there

- Implement incremental analysis for stats and sentiment
- Don't fail on missing data
- Put infrastructure in place
  * Host our instances in k8s / AWS lambda
  * Have a Travis CI example for self hosting

### Next Level

- Link to source (issue/PR) from data points
- Have an API to digest data into other applications for analysis
- …

[CoreNLP]: http]s://github.com/stanfordnlp/CoreNLP/blob/master/src/edu/stanford/nlp/sentiment/SentimentPipeline.java:
[Travis CI]: https://docs.travis-ci.com/user/status-images/
