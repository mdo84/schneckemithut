+++
date = "2017-05-26T22:25:02+02:00"
draft = false
title = "check_underreplicated_files"

+++



Sollte sich per Monitoring rausstellen, dass einige Files in einem HDFS underreplicated sind – lässt sich per CLI herausfinden, welche das sind:

su - <$hdfs_user>

bash-4.1$ hdfs fsck / | grep 'Under replicated' | awk -F':' '{print $1}' >> /tmp/under_replicated_files

-bash-4.1$ for hdfsfile in $(cat /tmp/under_replicated_files); do echo "Fixing $hdfsfile :" ; hadoop fs -setrep 3 $hdfsfile; done

Quelle:
https://community.hortonworks.com/articles/4427/fix-under-replicated-blocks-in-hdfs-manually.html

