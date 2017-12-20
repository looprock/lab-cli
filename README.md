Setup
-----
Create a configurations under ~/.python-gitlab.cfg based on: https://python-gitlab.readthedocs.io/en/stable/cli.html


Usage
-----
```bash
$ lab -h
usage: lab [-h] [-w] [-r RESULTS] [-s SEARCH] action [id]

positional arguments:
  action                what you want to do: list, jobs
  id                    project id

optional arguments:
  -h, --help            show this help message and exit
  -w, --watch           watch jobs
  -r RESULTS, --results RESULTS
                        Number of job results returned
  -s SEARCH, --search SEARCH
                        search keyword for list command
```

Examples
--------
```bash
$ lab list
build-images/docker - id: 77
build-images/java - id: 78
build-images/node - id: 76
foo/demo-issues - id: 200
tools/panel - id: 276
tools/admin - id: 183
tools/api - id: 275
...
```

```bash
$ lab list -s aws
apps/aws-test1 - id: 20
apps/aws-test2 - id: 29
apps/aws-test3 - id: 173
```

``` bash
$ lab jobs 197
        2017-10-31T22:14:38.347Z status: success, id: 17153, committer email: user1@company.com
        2017-10-31T22:12:56.269Z status: success, id: 17152, committer email: user1@company.com
        2017-10-31T22:09:40.447Z status: success, id: 17151, committer email: user1@company.com
        2017-10-31T22:07:25.433Z status: success, id: 17150, committer email: user1@company.com
        2017-10-31T21:49:42.774Z status: success, id: 17123, committer email: user1@company.com
$ lab jobs 197 -r 10
        2017-10-31T22:14:38.347Z status: success, id: 17153, committer email: user1@company.com
        2017-10-31T22:12:56.269Z status: success, id: 17152, committer email: user1@company.com
        2017-10-31T22:09:40.447Z status: success, id: 17151, committer email: user1@company.com
        2017-10-31T22:07:25.433Z status: success, id: 17150, committer email: user1@company.com
        2017-10-31T21:49:42.774Z status: success, id: 17123, committer email: user1@company.com
        2017-10-31T19:28:01.999Z status: success, id: 17085, committer email: user1@company.com
        2017-10-31T19:09:22.885Z status: success, id: 17084, committer email: user1@company.com
        2017-10-30T15:02:35.385Z status: success, id: 16982, committer email: user2@company.com
        2017-10-30T15:01:02.360Z status: success, id: 16981, committer email: user2@company.com
        2017-10-30T14:58:35.347Z status: success, id: 16980, committer email: user2@company.com
```

```bash 
$ lab jobs 197 -r 2 -w
** Now: 2017-12-20T15:09:37.791636
        2017-10-31T22:14:38.347Z status: success, id: 17153, committer email: user1@company.com
        2017-10-31T22:12:56.269Z status: success, id: 17152, committer email: user1@company.com
** Now: 2017-12-20T15:09:47.795308
        2017-10-31T22:14:38.347Z status: success, id: 17153, committer email: user1@company.com
        2017-10-31T22:12:56.269Z status: success, id: 17152, committer email: user1@company.com
^CINFO: exiting watch!
```
