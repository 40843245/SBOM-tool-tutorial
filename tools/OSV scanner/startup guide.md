# quickstart guide of OSV Scanner
## prequisite
Before you use this tool, you have to install

+ latest version of OSV scanner
+ terminal (often has been installed while installing OS)

To make it be more convenient to execute to use OSV scanner (a executable file),

I highly recommend to set the path as System Environment path then restart the computer to make the change effect.

Also you need to connect the network (via hotspot or Wi-Fi etc) since it scans in online mode (unless you tell the scanning tool to scan it in offline mode) 

## installation
You can install OSV scanner from [command line](https://google.github.io/osv-scanner/installation/) or [release page of OSV scanner](https://github.com/google/osv-scanner/releases).

### installation from [release page of OSV scanner](https://github.com/google/osv-scanner/releases)
Step 1:

go to [release page of OSV scanner](https://github.com/google/osv-scanner/releases)

Step 2:

On release page, scroll down to `New Contributors->Contributor` section then expand the `Assets` section.

<img width="862" height="392" alt="image" src="https://github.com/user-attachments/assets/4afd411b-2aea-4242-be56-9fde8dc00a67" />

Then check OS and proccessor architecture of the OS on your device, and install different version of OSV scanner according to them.

#### Examples
##### Example 1

For example,

My device is in Windows 2011 and 64-bit operating system, x64-based processor.

I should download one of two options (highlight as red box in below figure) by clicking its hyperlink

<img width="1724" height="784" alt="image" src="https://github.com/user-attachments/assets/72d74fee-dd02-4ca5-bbf5-8b5888c61bfc" />

### installation from [command line](https://google.github.io/osv-scanner/installation/)
See [installation page](https://google.github.io/osv-scanner/installation/), it mentions lots of different ways to install it.

## Performing a SBOM Test
### Scanning a source directory
#### Just echo the output on terminal
Step 1:

Open terminal. 

In terminal, type

```
osv-scanner scan -r <source-directory-path>
```

where 

`<source-directory-path>` is the source directory that will be scanned.
  
> [!NOTE]
> If you don't set it as System environment Path, you have to type the full path of the osv scanner executable file rather than `osv-scanner`.

> [!IMPORTANT]
> Here, you don't tell the scanning tool to scan it in offline mode, it scans in online mode, thus you need network while scanning.

#### looking the scanning report at web page
Step 1:

Open terminal. 

In terminal, type

```
osv-scanner scan -r <source-directory-path> --serve
```

where 

`<source-directory-path>` is the source directory that will be scanned.

Step 2:

Click the link (which is in url format) on the terminal

<img width="1867" height="578" alt="image" src="https://github.com/user-attachments/assets/fc3d9cc1-d9f6-4ac8-8b39-9c98183e4546" />

Then it will open a new wb page

<img width="950" height="506" alt="image" src="https://github.com/user-attachments/assets/5ba6a3e3-8750-4182-8c49-87f68484ebfc" />

you can see its detailed information on this scanning report.

> [!NOTE]
> If you don't set it as System environment Path, you have to type the full path of the osv scanner executable file rather than `osv-scanner`.

> [!IMPORTANT]
> Here, you don't tell the scanning tool to scan it in offline mode, it scans in online mode, thus you need network while scanning.

> [!IMPORTANT]
> When you execute the above command, OSV scanner will NOT ONLY scan it BUT ALSO binds the default IP address and default port on your host machine
>
> then generating a scanning report displayed at the web page that redirected from the given url on terminal.
>
> Since it is NOT allowed to use same sockets on same host machine at same time (O.S. its a common sense in network field),
>
> you can't execute the above command again until the previous task (started by executed above command) is successfully killed.
>
> Otherwise, you will see an error message on terminal (though it don't echo error message with red foreground color (and it's not easily noticed)
>
> See following example.

> [!TIP]
> One socket means `<ipAddress>:<portNumber>`
>
> socket = ipAddress ':' portNumber 

##### Wrong Examples
###### Wrong Example 1 -- Executing same task at same host machine at same time
When I execute 

```
"D:\SrcCode\osv-scanner_windows_amd64.exe" scan -r "D:\workspace\developing project (git)\CGSS8-pull-test\CGSSProject" --serve
```

at first time,

I will see a url that redirect to the web page displaying scanning reports as following figure illustrates.

<img width="1867" height="578" alt="image" src="https://github.com/user-attachments/assets/fc3d9cc1-d9f6-4ac8-8b39-9c98183e4546" />

Immediately, I executed same command again, then I see an error message

```
Failed to start server: listen tcp :8000: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.
```

<img width="1908" height="718" alt="image" src="https://github.com/user-attachments/assets/5ad271dd-00c7-4c11-b298-b9d7ab06e284" />

since the socket is already in use state.

## flags and options
See [commonly used flags and options](https://github.com/google/osv-scanner)

## demo video
referenced at [ref.md](https://github.com/40843245/SBOM-tool-tutorial/blob/main/attachments/tools/OSV%20scanner/demo/demo%20video/ref.md)
