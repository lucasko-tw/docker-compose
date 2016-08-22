Dockerfile of the Jupyter
=============================
[Let's see Dockerfile](https://github.com/lucasko-tw/docker-jupyter/blob/master/Dockerfile)


Configuration of Logstash 
=============================
To Modify the the remoting Host IP from Input (logstash.config)
It will migrate data to local's elasticsearch

	input {
	  elasticsearch {
	    hosts => "192.168.1.1:9200"
	 	index => "*" 
	 	docinfo => true
	  }
	}

	output {
	  elasticsearch { hosts => ["es-server:9200"] 
	   index => "%{[@metadata][_index]}"
	    document_type => "%{[@metadata][_type]}"
	    document_id => "%{[@metadata][_id]}"
	   }
	  
	}



docker-compose.yml for Jupyter-notebbook、anaconda、scikit-learn、elasticsearch、pyes
=============================

### To run the container
	docker-compose up

### To connect the website of Jupyter
	http://localhost:8888/tree

### To connect the head plugin of elasticsearch
	http://localhost:29200/_plugin/head/



