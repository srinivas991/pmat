# pmat - basic static analysis

### fingerprinting the malware

useful for searching on VirusTotal

sha256sum.exe wannacry.exe.malz

md5sum wannacry.exe.malz

### strings

floss.exe wannacry.malz.exe

### Import Address Table

peview

starts with MZ -> its an exe file

image_nt_headers -> image_file_header => shows the timedate stamp of when this is compiled

if that says 1992, then its probably wrong / maybe its a malware written in delphi (these always have time at 1992)

image_section_header .text -> here you will see virtual size and size of raw data

  if virtualsize >> raw -> probable that the exe is packed -> something to make a note of

section .rdata

  import_Address_table -> important
  
    this has all the Windows API calls that the exe is making

    https://malapi.io/ -> has the functions that are commonly used in malware -> functions in the import table which are here are worth scrutiny

packing

  indicators of packed malware

    raw data size in image_section_header .text is <<< virtual size
    very less number of imported functions in import table in section .rdata
    differences in the PE layout
