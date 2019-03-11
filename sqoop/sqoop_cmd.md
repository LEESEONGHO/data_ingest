quiz_1.
[training@localhost ~]$ sqoop import --connect jdbc:mysql://localhost/loudacre --username training --password training --query "select first_name,last_name from accounts where 1=1 and \$CONDITIONS" --target-dir /loudacre/accounts/user_info --split-by first_name

quiz_2.
[training@localhost ~]$ sqoop import --connect jdbc:mysql://localhost/loudacre --username training --password training --query "select first_name,last_name from accounts where 1=1 and \$CONDITIONS" --target-dir /loudacre/accounts/user_compressed --split-by first_name --as-parquetfile --compression-codec org.apache.hadoop.io.compress.SnappyCodec

quiz_3.
[training@localhost ~]$ sqoop import --connect jdbc:mysql://localhost/loudacre --username training --password training --query "select first_name,last_name from accounts where 1=1 and state='CA' and \$CONDITIONS" --target-dir /loudacre/accounts/CA_only --split-by first_name --as-parquetfile