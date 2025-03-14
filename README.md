# ExecWrap
Creates native executable which proxies the CLI arguments to another executable

## Why?
Python zip apps or bash scripts can't be natively executed on every platform. They rely on their host runtime executable like python or bash, which needs to be available. <br>
Besides, OS or posix library's exec calls don't support delegating the execution to the host runtime executables.
To solve this issue, we can create a native executable which will internally invoke the host runtime executable like python or bash and forward the CLI args to them.

## Usage
### Build your executable wrapper
```bash
$ meson setup build --name=myexec --exec=python --args='/usr/shader/app.pyz mysubcommand'
$ meson install -C build
```
> [!Note]
> The `--args` option takes a string and multiple arguments are specified by seperating them with single spaces only.
### Test the installed executable wrapper
```
$ ./myexec
```
