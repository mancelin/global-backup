# global-backup
Backup files and folders listed on a config file. Easily restore a backup.

**make_backup** allows you to copy very easily a list of files or folders and their path in a folder passed on parameter (or folder **BACKUP** if used without parameters).

The created folders end with a suffix according to date and version.

Edit **~/.make-backup** to configure the files to track.

**deploy_backup** allows you to restore a backup previously created with **make_backup**.

## Installation

* Clone or download this repository
```
    $ git clone git@github.com:mancelin/make-backup.git
```
* Add make-backup to your path, for example by editing ~/.bashrc
```
    $ cd global-backup
    $ echo "export PATH=`pwd`:$PATH" >> ~/.bashrc
```

## Quick start

* Edit **~/.global-backup**, adding one line per file or folder (full path)

  Add current folder to **~/.global-backup** :
```
    $ pwd >> ~/.global-backup
```

* run **make_backup** :
```
    $ make_backup NAME_BACKUP
```
The argument is optional, if not precised, **make_backup** will create the folder BACKUP, acoording to date and version.


## Use - make_backup

Use: make_backup \[OPTION..] [NAME_BACKUP]

Backup files and folders listed on ~/.global-backup to NAME_BACKUP_date_version or in BACKUP_date_version if used without parameters

Options:

  -c, --compress        Compress the backup in a .tar.gz
  
  -d, --dry             Dry run, print just all the commands that will be run by make_backup

  -h, --help            Display this help screen  help = """Use: make_backup \[OPTION..] [NAME_BACKUP]
  
  -v, --verbose         Print each command that will be run


## Use - deploy_backup

Use: deploy_backup \[OPTION..] [BACKUP]

Deploy backup files and folders and restore symlinks.

Options:

  -d, --dry             Dry run, print just all the commands that will be run by deploy_backup

  -h, --help            Display this help screen

  -v, --verbose         Print each command that will be run


## Example

Content **~/.global-backup** :
```
    $ cat ~/.global-backup

    /home/user/.global-backup
    /home/user/2 words
    /home/user/cmd
```

Run **make_backup** :
```
    $ make_backup example_backup
```

This command produces the folder example_backup_21_01_2017_v1

Content of our first backup :

```
    $ tree -a example_backup_2017_1_21_v1/
    example_backup_2017_1_21_v1/
    ├── .backuped
    └── home
        └── user
            ├── 2 words
            │   └── d.txt
            ├── config.git
            │   └── cmd
            │       ├── catbash
            │       ├── make_backup
            │       ├── tarv
            │       ├── tarvc
            │       └── up_perl
            └── .global-backup
```

Running it again will produce example_backup_21_01_2017_v2, etc.

If we run it the next day, it will produce the folder example_backup_22_01_2017_v1

## Licence
GNU GENERAL PUBLIC LICENSE
