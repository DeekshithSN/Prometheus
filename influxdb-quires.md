## Overall Panel 

query to get success build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'SUCCESS' OR "build_result" = 'CompletedSuccess' ) AND $timeFilter 
```
query to get failed build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'FAILURE' OR "build_result" = 'CompletedError' ) AND $timeFilter 
```
query to get aborted build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'ABORTED' OR "build_result" = 'Aborted' ) AND $timeFilter 
```
query to get unstable build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'UNSTABLE' OR "build_result" = 'Unstable' ) AND $timeFilter 
```
