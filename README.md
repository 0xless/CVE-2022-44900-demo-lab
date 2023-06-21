# CVE-2022-44900 Demo lab
Demo webapp vulnerable to [CVE-2022-44900](https://nvd.nist.gov/vuln/detail/CVE-2022-44900).

CVE-2022-44900 is a directory traversal vulnerability in SevenZipFile.extractall() function of the python library py7zr version 0.20.0 and earlier that allow attackers to read and write arbitrary files on the local machine via malicious 7z file extraction.

To exploit CVE-2022-44900 vulnerability an attacker needs to create a malicious 7z archive containing a symlink to achieve an arbitrary file read and a file with a path traversal payload as name to achieve an arbitrary file write.

More details at: https://lessonsec.com/cve/cve-2022-44900/  
Use `slip` to generate malicious archives: https://github.com/0xless/slip

## Getting started
To run the vulnerable webapp you can either create a docker container, or run the server only.  
In case you decide to run the server only, you need to run:
```
pip3 install py7zr==0.20.0
```
To install the vulnerable version of py7zr.

Then simply run the application with:
```
python3 slipper.py
```
And the webapp will be available at `localhost:9999`.

To create the container, use the dockerfile to create the `slipper` image.
Then create a container with `host` network and exposing port `9999`. Just like the other installation method, this will allow you to reach the webapp at `localhost:9999`.

The website will look like this:
![homepage-screenshot](https://user-images.githubusercontent.com/78535423/215351809-2c0b8a98-cb27-48af-84f7-0714ac49221d.png)

Now you can extract files and attempt exploiting this lab.

## Notes
The webapp is not meant to be open to the public, it is probably vulnerable to some other vulnerabilities and it doesn't handle every error correctly (like you would expect form a normal website).
Make sure to use this software safely.

## License

This project is licensed under the GPL-3.0 [License](https://github.com/0xless/CVE-2022-44900-demo-lab/blob/main/LICENSE).
