# concater
Easily downloads concatenates remote and local files into one single file.


####To use concater, you need to create a json file first that has a format like this:
```json
{
    "concater" : [
        {
            "remote" : [
                "file url 1",
                "file url 2",
                "file url ....",
                "file url n"
            ],
            "local" : {
                "absolute-path-of-the-folder" : [
                    "filename 1",
                    "filename 2",
                    "filename ...",
                    "filename n",
                ]
            },
            "vendor-file" : "full-path-of-your-vendor-file"
        },
        {
            /* repeat above ... */
        }
    ]
}
```

####Example concater.json:
```json
{
    "concater" : [
        {
            "remote" : [
                "https://code.jquery.com/jquery-3.1.1.min.js",
                "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"
            ],
            "local" : {
                "D:/dev/www/dev.ghabxph.info/public/assets/dev/js" : [
                    "default.js",
                    "somejs.js"
                ]
            },
            "vendor-file" : "D:/dev/www/dev.ghabxph.info/public/assets/prod/vendor.js"
        },
        {
            "remote" : [
                "https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css",
                "https://raw.githubusercontent.com/daneden/animate.css/master/animate.css"
            ],
            "local" : {
                "D:/dev/www/dev.ghabxph.info/public/assets/dev/css" : [
                    "default.css"
                ]
            },
            "vendor-file" : "D:/dev/www/dev.ghabxph.info/public/assets/prod/vendor.css"
        }
    ]
}
```

####Then run:
`php concater concater.json`

It will display the following sample output...
```



,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

   ████╗ ████╗ ███╗  ██╗ ████╗ ████╗ ██████╗█████╗█████╗
  ██╔══╝██╔═██╗████╗ ██║██╔══╝██╔═██╗╚═██╔═╝██╔══╝██╔═██╗
  ██║   ██║ ██║██╔██╗██║██║   ██████║  ██║  ███╗  █████╔╝
  ██║   ██║ ██║██║╚████║██║   ██╔═██║  ██║  ██╔╝  ██╔═██╗
  ╚████╗╚████╔╝██║ ╚███║╚████╗██║ ██║  ██║  █████╗██║ ██║
   ╚═══╝ ╚═══╝   ╚═╝ ╚═╝ ╚═══╝╚═╝ ╚═╝  ╚═╝  ╚════╝╚═╝ ╚═╝
         Developed by Gabriel Lucernas Pascual
               Since December 17, 2016
                   Version 1.0.0
         Site URL: http://ghabxph.info/concater
    Repository URL: https://github.com/ghabxph/concater

\``````````````````````````````````````````````````````````

  ################################################################
  ##
  ##   Preparing things for your vendor.js
  ##
  ################################################################

Downloading and concatinating remote files...
------------------------------------------------------

    Downloading jquery-3.1.1.min.js...
    jquery-3.1.1.min.js has been downloaded successfully.
    Downloading bootstrap.min.js...
    bootstrap.min.js has been downloaded successfully.

Concatenating local files...
------------------------------------------------------

    Adding default.js...
    default.js has been added!
    Adding somejs.js...
    somejs.js has been added!


        ###################################################
        ## Concatenating remote files and local files...
        ##
        ## Done concatenating remote files and local files. Will write this to your vendor.js
        ##
        ## Creating/Opening vendor.js
        ##
        ## Overwritting existing vendor.js file
        ##
        ## Operations on vendor.js file is done. Now closing this file.
        ##
        ###################################################

8  88            8""""8                     8   8
8   8 eeeeeee    8    8 eeeee eeeee eeee    8   8 eeee eeeee  eeee
8e    8  8  8    8e   8 8  88 8   8 8       8eee8 8    8   8  8
88    8e 8  8    88   8 8   8 8e  8 8eee    88  8 8eee 8eee8e 8eee
88    88 8  8    88   8 8   8 88  8 88      88  8 88   88   8 88
88    88 8  8    88eee8 8eee8 88  8 88ee    88  8 88ee 88   8 88ee 88 88 88
------------------------ I ' M  D O N E  H E R E ------------------------

  ################################################################
  ##
  ##   Preparing things for your vendor.css
  ##
  ################################################################

Downloading and concatinating remote files...
------------------------------------------------------

    Downloading bootstrap.min.css...
    bootstrap.min.css has been downloaded successfully.
    Downloading animate.css...
    animate.css has been downloaded successfully.

Concatenating local files...
------------------------------------------------------

    Adding default.css...
    default.css has been added!


        ###################################################
        ## Concatenating remote files and local files...
        ##
        ## Done concatenating remote files and local files. Will write this to your vendor.css
        ##
        ## Creating/Opening vendor.css
        ##
        ## Overwritting existing vendor.css file
        ##
        ## Operations on vendor.css file is done. Now closing this file.
        ##
        ###################################################

8  88            8""""8                     8   8
8   8 eeeeeee    8    8 eeeee eeeee eeee    8   8 eeee eeeee  eeee
8e    8  8  8    8e   8 8  88 8   8 8       8eee8 8    8   8  8
88    8e 8  8    88   8 8   8 8e  8 8eee    88  8 8eee 8eee8e 8eee
88    88 8  8    88   8 8   8 88  8 88      88  8 88   88   8 88
88    88 8  8    88eee8 8eee8 88  8 88ee    88  8 88ee 88   8 88ee 88 88 88
------------------------ I ' M  D O N E  H E R E ------------------------



    DO SOMETHING PRODUCTIVE :)
```

Update as of December 18 2016: 9:22 PM
    - Concater can watch file now. Simply add --watch or -watch command
    - Concater has a caching mechanism for remote files so that it will not download files automatically, but instead, save it in a cache file called remote.--vendor-file-name-- (something like that), under your vendor folder.
        - Cache can be bypassed and force the downloading of files using -nc or --no-cache command.
        - --no-cache will not disable caching, but instead, it will bypass reading the cache created. Therefore, concater will still cache remote files in your remote.--vendor-file-name--.