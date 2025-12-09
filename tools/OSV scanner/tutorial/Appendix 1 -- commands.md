# Appendix 1 -- commands
## objectives
You will know 

  + meaning of some commonnly used commands
  + meaning of some commonnly used flags and options

## Appendix 1.1 -- some commonnly used commands
### scan
The `scan` command can scan a source directory or a container in `online` mode. 

> [!IMPORTANT]
> When scanning it with scan command (and not use `--offline` option), you need to connect the network,
>
> letting the OSV scanner tool connect to OSV database.

#### source directory
One can use scan a source directory by simply adding the full absolute path of source directory.

For example,

```
osv-scanner scan -r "D:\workspace\developing project (git)\CGSS8-pull-test\CGSSProject" --serve
```

will scan the full 

The command scan can be used with these options. 

| options | (abbreviated) flags | description |
| :-- | :-- | :-- |
| `--serve` | NULL | generate a scanning report (represented by html) that is displayed on web page on the server |
| `--recursive` | `-r` | scan the source directory recursively (i.e. scan all descendants of the source directory) | 
| ` --no-ignore`| NULL | also scan files that would be ignored by `.gitignore` |
| `--include-git-root` | NULL | include scanning git root (non-submoduled) repositories |
| `--lockfile` | `-L` | scan package lockfile on this path |

where

NULL means nothing, there is no such flag that corresponds to the option (if it is in `(abbreviated) flags` column)

##### Examples
###### Example 1

```
osv-scanner scan -r "D:\workspace\developing project (git)\CGSS8-pull-test\CGSSProject" --serve
```

will scan the descendant of source directory "D:\workspace\developing project (git)\CGSS8-pull-test\CGSSProject" using OSV database amd 

generating a scanning report at `http://localhost:8000/` (assuming the default port is 8000 (when installing OS, it defaults to 8000)) url.

###### Example 2

```
osv-scanner scan -L "D:\workspace\developing project (git)\CGSS1-pull-test\CGSSProject\appsettings.json.lockfile"
```

will scan packages from the lockfile located at `D:\workspace\developing project (git)\CGSS1-pull-test\CGSSProject\appsettings.json.lockfile`

### --help
The help command (`--help`) appended at the end will list the usage, description and options of the command. 

## references
[Official GitHub Web Page of OSV Scanner](https://github.com/google/osv-scanner)
