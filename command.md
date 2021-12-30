#  #
rs.printSlaveReplicationInfo()
rs.status()
rs.conf()
db.getReplicationInfo()
db.oplog.rs.find()

rs.add({ host: "<IP>:<PORT>", priority: 0, votes: 0, hidden: true })
rs.remove("<IP>:<PORT>")

cfg = rs.conf();
cfg.members[4].priority = 0
cfg.members[4].votes = 0
cfg.members[4].hidden = false
print(cfg)
---
rs.reconfig(cfg)

mongod --config /etc/mongod.conf --fork
ps -ef |grep mongo
