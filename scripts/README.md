=Setup Local Repo=

The get_repo.sh downloads all the packages and parcel that used for installing the Cloudera manager and CDH componments.

Componments
- centos repository
    + Operating system packages
    + Update packages
- Cloudera Manager Packages
    + Jdk
- CDH parcels
    +
- Epel repository
- Kakfa Parcel
- jce

=How to you get_repo.sh=

The get repo required 2 arguments, the first arg is the centos or Redhat operating verison thatis used to install the Cloudera Manager on e.g. 6.8, 7.2. The second argument is the CHD version will be installed e.g. 5.9.1, 5.11.

The script when complete will create a file cloudera_repos<os verison>-<cdh version>.tar.gz

```
$ get_repo.sh 7.2 5.11.
```


==Setup cloudera playbook==
The following configuration is required to enable the local repository for cloudera playbook.

1. Run get_repo.sh to download the required packages and parcel.(note: internet is required to run the scripts).
2. move the compressed file created by get_repo.sh to the directory of the cloudera-play/scripts/
3. Configure that following files:
    - group_vars/local_repo_server
        + use_local_repo: true
        + setup_local_repo: true
        + local_repo_server: <hostname that contains the playbook>
        + local_repo_port: 8000 #change port or if port 8000 is used 

