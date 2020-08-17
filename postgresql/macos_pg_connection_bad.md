### MacOS Homebrew PG::ConnectionBad issue

#### Problem

Many times over last years I've been in a situation when my macbook shuts down due to some problem and PostgreSQL couldn't shutdown itself properly. As a result, on the boot Postgres couldn't start and when you try to run `rails server` or any other app that depends on PostgreSQL - you get something like this:
```bash
/Users/raeno/.rbenv/versions/2.6.3/lib/ruby/gems/2.6.0/gems/pg-1.1.4/lib/pg.rb:56:in `initialize': could
not connect to server: No such file or directory (PG::ConnectionBad)
        Is the server running locally and accepting
        connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```

Source of the problem is obvious -  PostgreSQL hasn't removed pid file - but I always had trouble trying to remember where this PID file is located.

Here's the fix for my future self ( applies to PostgreSQL installed via Homebrew ):

```bash
rm -f /usr/local/var/postgres/postmaster.pid
brew services restart postgresql
```

