# AWS Extender CLI

AWS Extender CLI is a command-line script to test S3 buckets as well as Google Storage buckets and Azure Storage containers for common misconfiguration issues using the boto/boto3 SDK library.

## Install

```ShellSession
makepkg -si && aws-extender-cli -v
```

## CLI Arguments

Below is a description of supported arguments:

| Argument | Description | Required |
|----------|:-------------:|:-------------:|
| -h, --help | Show a help message and exit | False |
| -f, --filepath | The path of a bucket names list | False* |
| -b, --bucket | The name of the bucket to test | False* |
| -w, --wordlist | A wordlist filepath | False |
| -o, --output | An output filename | False |
| -k, --keys | The path of your credentials file | False |
| -s, --service | the name of the storage service ("S3", "GS", or "Azure") | True |
| -v, --version | Show the version of the script | False |


#### Notes:
* Mutually exclusive arguments are denoted by an asterisk.
* The `-k/--keys` argument expects the filepath of your [AWS](https://console.aws.amazon.com/iam/home?#/security_credential)/[GS](https://cloud.google.com/storage/docs/migrating#keys) keys. The keys are expected to be in the following format:
```
aws_access_key_id=XXXXXXXXXXXXXXXXXXXX
aws_secret_access_key=XXXXXXXXXXXXXXXXXXXXXX
```


## Example Usage (Installing it):


```bash
aws-extender-cli -s s3 -b mybucketname
```

```bash
aws-extender-cli -s S3 -b flaws.cloud -k keys.csv
```

```bash
aws-extender-cli -s s3 -b mybucketnam -w /usr/share/wordlists/darkc0de.lst -o output.txt
```

## Example Usage (With Installing it):

```bash
aws_extender_cli.py -s s3 -b mybucketname
```

```bash
aws_extender_cli.py -s S3 -b flaws.cloud -k keys.csv
```

```bash
aws_extender_cli.py -s s3 -b mybucketnam -w /usr/share/wordlists/darkc0de.lst -o output.txt
```


## Usage

The script can be used to test individual buckets, or to test a list of buckets from a file. The `-s` argument is required and specifies the service to test. The `-b` argument specifies the bucket to test, and the `-f` argument specifies the file containing a list of buckets.

The `-k` argument specifies the path to a file containing your AWS/GS credentials. The credentials are expected to be in the following format:

```
aws_access_key_id=XXXXXXXXXXXXXXXXXXXX
aws_secret_access_key=XXXXXXXXXXXXXXXXXXXXXX
```

The `-w` argument specifies a wordlist to use for enumeration attacks. The wordlist should contain a list of file names or paths, one per line.

The `-o` argument specifies an output file to write the results to. If no output file is specified, the results will be printed to the console.

## Features

* **S3 bucket testing:** 
The script can test S3 buckets for common misconfiguration issues, such as:
* Public read access
* Public write access
* Missing bucket policies
* Missing bucket logging
* Missing bucket lifecycle rules
* Missing bucket versioning
* Missing bucket encryption
* Missing bucket CORS configuration
* Missing bucket website configuration
* Missing bucket notification configuration
* Missing bucket tagging

* **Google Storage bucket testing:**
The script can test Google Storage buckets for common misconfiguration issues, such as:
* Public read access
* Public write access
* Missing bucket policies
* Missing bucket logging
* Missing bucket lifecycle rules
* Missing bucket versioning
* Missing bucket encryption
* Missing bucket CORS configuration
* Missing bucket website configuration
* Missing bucket notification configuration
* Missing bucket tagging

* **Azure Storage container testing:**
The script can test Azure Storage containers for common misconfiguration issues, such as:
* Public read access
* Public write access
* Missing container policies
* Missing container logging
* Missing container lifecycle rules
* Missing container versioning
* Missing container encryption
* Missing container CORS configuration
* Missing container website configuration
* Missing container notification configuration
* Missing container tagging

* **Wordlist enumeration:**
The script can be used to enumerate objects in buckets using a wordlist.

* **Output to file:**
The script can output the results to a file.

## Contributing

Contributions are welcome! If you have any suggestions or bug reports, please open an issue on the GitHub repository.

## Disclaimer

This script is provided for educational purposes only. It should not be used to harm or exploit others. The author is not responsible for any misuse of this script.
