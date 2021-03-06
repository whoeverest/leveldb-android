# LevelDB for Android

This is a Java wrapper for the amazing LevelDB
(https://code.google.com/p/leveldb/) by Google.

LevelDB supports only ARM and X86 ABIs. MIPS is not supported. (Someone
implement port/atomic_pointer.h for MIPS.)

Currently it does not use Snappy for data compression. (There is really no
need for this in Android, i.e. it's unnecessary overhead.) Only the basic API
is supported.

LevelDB's native log output is tagged: "org.leveldb:N"

## Example

```java
  LevelDB levelDB = new LevelDB("path/to/leveldb", true);
  
  levelDB.put("leveldb", "Is awesome!");
  String value = levelDB.get("leveldb");
  leveldb.put("magic", new byte[] { 0, 1, 2, 3, 4 });
  byte[] magic = levelDB.getBytes("magic");
  levelDB.close(); // closing is a must!
```

## TODO

* WriteBatch API
* Iteration API
* LevelDB#close() in Object#finalize() (?)
* Compaction API
* Snapshot API
* Greater configurability
* Snappy compression
* Support Table API (?)
