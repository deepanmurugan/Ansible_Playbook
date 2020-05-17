# Rolling upgrade of ELK stack

ansible-playbook -i inv main.yml

### Steps in Upgrading Logstash: upgrade_logstash.yml
```
1. Pre download the deb package
2. Make sure logstash version is installed in the node and the version installed is less than the one you are trying to install
3. Backup important config files
4. Stop logstash service
5. Upgrade logstash
6. Get the logstash version and compare with the one we are trying to install, to make sure it's installed properly
7. Start logstash
8. Wait for logstash to come up
9. Go for the next node
```

### Steps in Upgrading Elasticsearch: upgrade_es.yml
```
1. Pre download the deb package
2. Make sure ES version is installed in the node and the version installed is less than the one you are trying to install
3. Make sure ES is started
4. Make API calls to Disable allocation of primaries and Perform a synced flush (only on data nodes)
5. Stop ES service
6. List all plugins installed
7. Remove all installed plugins
8. Make sure all plugins are removed and Upgrade ES. Incase plugins are not removed, you cannot upgrade plugins, you have to again downgrade ES, remove plugins, upgrade ES and reinstall new plugins.
9. Validate if new ES version is installed
10. Install all plugins except x-pack since x-pack is default in 6.8.X version
11. Start ES
12. Make sure node comes up
13. Make sure node joins existing cluster
14. Enable allocation of primaries on ES Node
15. Wait for the cluster to become green before going to next node
```

### Steps in Upgrading Kibana: upgrade_kibana.yml
```
1. Backup all the saved objected in the Kibana UI. (Optional and needed only if you want to migrate any saved objects in        kibana).
   Login to Kibana UI
   Navigate to Management.
   Go to "Saved Objects".
   Click on export button on the top of page. 
2. Pre download the deb package
3. Make sure kibana version is installed in the node and the version installed is less than the one you are trying to install
4. Backup important config files
5. Stop kibana service
6. Upgrade kibana
7. Get the kibana version and compare with the one we are trying to install, to make sure it's installed properly
8. Start kibana
9. Wait for kibana to come up
10. Go for the next node
```
