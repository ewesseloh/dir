# Dir - Directory Scanner

[![Build Status](https://travis-ci.org/crysalead/dir.png?branch=master)](https://travis-ci.org/crysalead/dir) [![Scrutinizer Quality Score](https://scrutinizer-ci.com/g/crysalead/dir/badges/quality-score.png?s=1ef861497b4e3394b8141160e5f3907e45ea2149)](https://scrutinizer-ci.com/g/crysalead/dir/) [![Code Coverage](https://scrutinizer-ci.com/g/crysalead/dir/badges/coverage.png?s=ef6f07deaccac56d0f4c1591fc99761fed854461)](https://scrutinizer-ci.com/g/crysalead/dir/)

Dir is a small library which allows to perform some recursive operations on directories.

## `Dir::scan()`

Gets all nested directories and/or files present inside a directory.

```php
$files = Dir::scan('my/dir',       // Can be a string path of an array of string paths
    [
        'include' => '*.txt',      // Can be an array of includes
        'exclude' => '*.save.txt', // Can be an array of excludes
        'type'    => 'file'        // Can be an array of types, possible values:
                                   // `'file'`, `'dir'`, `'executable'`, `'link'`, `'readable'`, `'writable'`
        'skipDots'       => true,  // Keeps '.' and '..' directories in result
        'leavesOnly'     => true,  // Keeps only leaves
        'followSymlinks' => true,  // Follows Symlinks
        'recursive'      => true   // Scans recursively
    ]
);
```

## `Dir::copy()`

Copies a directory with files recursively into a destination folder.

```php
$files = Dir::copy('my/dir',       // Can be a string path of an array of string paths
    'my/destination',              // A destination path (string only)
    [
        'mode'           => 0755,  // Mode used for directory creation
        'childsOnly'     => false, // Copies the file inside 'my/dir' if `true`, otherwise `dir` will be
                                   // added as the root directory.
        'followSymlinks' => true,  // Follows Symlinks
        'recursive'      => true   // Scans recursively
    ]
);
```

## `Dir::remove()`

Removes a directory and all its content recursively.

```php
$files = Dir::remove('my/dir',     // Can be a string path of an array of string paths
    [
        'followSymlinks' => false, // Follows Symlinks
        'recursive'      => true   // Scans recursively
    ]
);
```

## `Dir::tempnam()`

Creates a temporary folder (like the `tempnam()` function but for directories).

```php
$files = Dir::tempnam(sys_get_temp_dir(), 'mytmp');
```
