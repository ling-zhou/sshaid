sshaid
======
```
$ sshaid
usage: sshaid <action> [options] [cmd] [args]
use 'sshaid {help | h} <action>' to print help for a specific action

actions:
    help (h)
    ssh
    scp
    rsync (rs)

common-options:
    -H hosts-file
        line-format: host:user:password:port, never be with -h, no defaults.
    -h host:user:password:port
        never be with -H, no defaults.
    -u default-user
        optional, defaults to 'root'.
    -p default-password
        optional, defaults to 'x'.
    -P default-port
        optional, defaults to '22'.
    -d
        optional, prints debug info.
    -k
        optional, keeps sequence of output same as the order of input,
        normally the output of a job will be printed as soon as the job completes.
    -q
        optional, suppresses extra information for sshaid, such as sshaid prompt and debug info.
    -j N
        optional, runs up to N jobs in parallel, 0 means as many as possible,
        defaults to one job per CPU.
    -t duration
        optional, time out in seconds, if the command runs for longer than duration
        it will get killed, defaults to 60s.
    --hsep single-line-host-separator
        optional, defaults to ':'.
    --csep single-line-comment-separator
        optional, defaults to '//'.
    --proxy http_proxy_ip:http_proxy_port
        optional, no defaults.

attentions:
    1. options can not be combined, legal examples: '-d -k', '-t 2', illegal examples: '-dk', '-t2'.
    2. '-H' and '-h' can not be used at the same time.
    3. USER specified by -u can be overridden by USER in host:USER:password:port.
    4. PASSWORD specified by -p can be overridden by PASSWORD in host:user:PASSWORD:port.
    5. PORT specified by -P can be overridden by PORT in host:user:password:PORT.
    6. host-separator is needed if the member in between is not specified,
       for example: host::password
            in this case, default user will be used, and it can be overridden by -u.
    7. user defined host-separator must be specified if PASSWORD contains ':'.
       for example: 1.2.3.4_@_root_@_my:/passwd_@_22 // real comment
       # sshaid ... --hsep '_@_' ...
    8. user defined single-line-comment-separator must be specified if PASSWORD contains '//'.
       for example: 1.2.3.4:root:my//passwd:22 !@# real comment
       # sshaid ... --csep '!@#' ...


sshaid is an automation tool based on ssh, sshpass, and gnu parallel, it can be used to:
    1. scp/rsync file/dir(s) from local to remote, or in reverse.
    2. ssh into host(s)(and execute command(s)).

report bug(s) to <zhou.0@foxmail.com>.

```
