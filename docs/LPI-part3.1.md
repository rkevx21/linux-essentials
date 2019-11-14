# Topic 3: The Power of the Command Line

## 3.1 Archiving Files on the Command Line

### Lecture: Files and Directories

- **tar** - Tape Archive

`c` - create archive

`x` - extract archive

`r` - append to an archive

`t` - list the contents of an archive

`f` - read from or write to a file

`tar cf test.tar test_file*`

`tar xf test.tar`

`tar rf test.tar file_* ]`

`tar xf test.tar --wildcards 'test_file_7'`

`tar --delete ---file=test.tar file123`


### Lecture: Archives and Compression

Is the process of reducing the amount of storage that files or archives consume. Typically used during archiving to reduce the storage space needed for archives. 
				
- **gzip** - the default compression used by tar via (-z), a good balance of speed and size reduction
- **bzip2** - an alternative compression algorithm, typically slower than gzip to higher compression
- **zip** - the algorithm used by the zip command, and all-in-one compression and archiving utility

## Hands-On Lab

### Archiving Files on the Command Line

*Create a Normal Archive*
1. Use the following command to create a tarball of the ~/Practice folder named archive.tar:
		`tar cvf archive.tar Practice/`

*Add the File **~/extra.txt** to **archive.tar***
1. Use the following command to add the file ~/extra.txt to the existing tarball:
		`tar rf archive.tar extra.txt`

*Create a Compressed Archive*
1. Now create another tarball, but this time, compress it during creation with the following command:
		`tar czf archive.tgz Practice/`

*Compress the Normal Archive*
1. Use the gzip utility to compress the first tarball (archive.tar) with maximum compression:
		`gzip -9 archive.tar`
2. This will compress the file and rename it archive.tar.gz.

*Extract the File **Practice/Test/version.txt** from **archive.tar.gz***
1. Use the following command to extract the file Practice/Test/version.txt from the compressed archive archive.tar.gz:
		`tar xzf archive.tar.gz Practice/Test/version.txt`
2. This will extract the file to the existing path and overwrite the file if it exists.
