# aufs-example

    mkdir mnt

    sudo mount -t aufs -o dirs=./writable:./readonly none ./mnt

## create new file

    cd mnt

    sudo touch newfile

    cd -

    ls ./readonly
    readme

    ls ./writable
    newfile  writeme


## modify readonly file

    cd mnt

    sudo vi readme
    hello readme
    newline

    cd -

    cat readonly/readme
    hello readme

    ls ./readonly
    readme

    ls ./writable
    newfile  readme  writeme

    cat ./writable/readme
    hello readme
    newline

## delete file

    cd mnt

    sudo rm readme

    ls
    newfile  writeme

    cd -

    ls ./readonly
    readme

    ls ./writable
    newfile  writeme

    ll ./writable
    total 20
    drwxr-xr-x 4 root root 4096 Oct 18 09:37 ./
    drwxr-xr-x 6 root root 4096 Oct 18 09:26 ../
    -rw-r--r-- 1 root root    0 Oct 18 09:28 newfile
    -r--r--r-- 2 root root    0 Oct 18 09:27 .wh.readme
    -r--r--r-- 2 root root    0 Oct 18 09:27 .wh..wh.aufs
    drwx------ 2 root root 4096 Oct 18 09:27 .wh..wh.orph/
    drwx------ 2 root root 4096 Oct 18 09:27 .wh..wh.plnk/
    -rw-r--r-- 1 root root   13 Oct 18 09:26 writeme