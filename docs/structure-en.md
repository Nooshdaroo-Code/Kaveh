# Kaveh Data Structure
The output of the Kaveh project is available in four files located in the root directory of this repository.

|File Name|Usage|
|--|--|
|full.json|Full version|
|mini.json|Lightweight version (recommended)|
|micro.json|Ultra-light version|
|VERSION|Current version code|

Each of these files will be explained below.

## Full Version (full.json)
This file provides the most complete version of Kaveh’s output in indented format. The file structure is as follows:
```
{
  "version": VERSION,
  "docs": {
    MALWARE_CLASS_1: MALWARE_CLASS_1_URL,
    MALWARE_CLASS_2: MALWARE_CLASS_2_URL,
    MALWARE_CLASS_3: MALWARE_CLASS_3_URL,
    ...
  },
  "malware": [
    {
      "sha256_hash": FILE1_SHA256_HASH,
      "sha1_hash": FILE1_SHA1_HASH,
      "md5_hash": FILE1_MD5_HASH,
      "detection": [
        MALWARE_CLASS_1,
        MALWARE_CLASS_2,
        ...
      ]
    },
    {
      "sha256_hash": FILE2_SHA256_HASH,
      "sha1_hash": FILE2_SHA1_HASH,
      "md5_hash": FILE2_MD5_HASH,
      "detection": [
        MALWARE_CLASS_3,
        ...
      ]
    },
    ...
  ]
}
```

### Main Section Definition

|Name|Type|Description|
|--|--|--|
|`version`|string|Version|
|`docs`|object|Links to malware category docs|
|`malware`|array|Array of malware samples|

### docs Section Definition
|Name|Type|Description|
|--|--|--|
|MALWARE_CLASS_N|string|Name of malware category|
|MALWARE_CLASS_N_URL|string|URL to the category documentation|

### malware Section Definition
|Name|Type|Description|
|--|--|--|
|`sha256_hash`|string|SHA256 hash of the malware|
|`sha1_hash`|string|SHA1 hash of the malware|
|`md5_hash`|string|MD5 hash of the malware|
|`detection`|array|Array of detected malware category names|
|MALWARE_CLASS_N|string|Name of the malware category|

> **Note**:
It is guaranteed that for every detectable malware category, there is a corresponding link with the same name in the `docs` object.

## Lightweight Version (mini.json)
This file includes all contents of the full version except for `sha1_hash` and `md5_hash`, and is not indented. This version is recommended for use in secondary applications.  
The file structure is as follows:
```
{
  "version": VERSION,
  "docs": {
    MALWARE_CLASS_1: MALWARE_CLASS_1_URL,
    MALWARE_CLASS_2: MALWARE_CLASS_2_URL,
    MALWARE_CLASS_3: MALWARE_CLASS_3_URL,
    ...
  },
  "malware": [
    {
      "sha256_hash": FILE1_SHA256_HASH,
      "detection": [
        MALWARE_CLASS_1,
        MALWARE_CLASS_2,
        ...
      ]
    },
    {
      "sha256_hash": FILE2_SHA256_HASH,
      "detection": [
        MALWARE_CLASS_3,
        ...
      ]
    },
    ...
  ]
}
```
## Ultra-light Version (micro.json)

This file contains only the MD5 hashes of malware and is not indented. This version is not recommended unless extreme optimization is required.  
The file structure is as follows:
```
{
  "version": VERSION,
  "malware": [
    FILE1_MD5_HASH,
    FILE2_MD5_HASH,
    ...
  ]
}
```

## Version File (VERSION)
This file indicates the current version of Kaveh's data. The version format is the release date in the format `YYYYMMDD`. Developers can compare their current version with the contents of this file to check if a newer version is available before updating the desired JSON file.