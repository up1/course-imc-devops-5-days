# [Backup and Restore](https://www.elastic.co/guide/en/elasticsearch/reference/current/snapshot-restore.html) data in Elasticsearch cluster
* File
* Amazon S3
* Hadoop Distributed File System (HDFS)
* Azure Storage

## 1. Create backup/repository with File system
```
PUT _snapshot/${backup}
{
  "type": "fs",
  "settings": {
    "location": "my_fs_backup_location",       
    "compress": true
  }
}
```

## 2. Take snapshot or backup
```
PUT /_snapshot/${backup}/${SNAPSHOT_NAME}?wait_for_completion=true

PUT _snapshot/${backup}/${SNAPSHOT_NAME}
{
  "indices": "index-1*,index-2,...",
  "ignore_unavailable": true,
  "include_global_state": false,
  "partial": false
}
```

## 3. Restore from Snapshot
```
POST _snapshot/${backup}/${SNAPSHOT_NAME}/_restore

POST _snapshot/${backup}/${SNAPSHOT_NAME}/_restore
{
  "indices": "data_stream_1,index_1,index_2",
  "ignore_unavailable": true,
  "include_global_state": false,              
  "rename_pattern": "index_(.+)",
  "rename_replacement": "restored_index_$1",
  "include_aliases": false
}
```

## 4. Monitoring snapshot and restore progress

```
GET _snapshot/_all
GET _snapshot/${backup}/_current
GET _snapshot/${backup}/${SNAPSHOT_NAME}
```
Status
```
GET _snapshot/_status
GET _snapshot/${backup}/_status
GET _snapshot/${backup}/${SNAPSHOT_NAME}/_status
```

Delete snapshot
```
DELETE _snapshot/${backup}/${SNAPSHOT_NAME}
```
