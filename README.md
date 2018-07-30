# WordCount Example Hadoop 3.0.3
### Installing Hadoop
To install Hadoop and set System Variable follow: https://github.com/AdityaSinghRathore/HadoopLinuxMint/blob/master/main.pdf


### Wordcount example on Hadoop 3.0.3 using Python code over Mapreduce Streaming
1. Firstly we need to start our hadoop cluster.  
```$ start-all.sh```

Or,  
```$ start-dfs.sh```  Then do  ```$ start-yarn.sh```  

2. Code the mapper in python (code files above).
```$ touch mapper.py```  
```$ vim mapper.py```  

![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/1mapper.png)  
![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/2mappercode.png)  

3. Writing a sample text file.
```$ touch sample.txt```  
```$ vim sample.txt```  

![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/3samplecre.png)
![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/4samplewrite.png)

4. Testing the Mapper code on above sample file.
```$ cat sample.txt | python mapper.py```

![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/5mapperrunloc.png)

5. Creating and coding the reducer.  
```$ touch reducer.py```  
```$ vim reducer.py```  

![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/6reducercre.png)
![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/7reducrimple.png)

6. SSH to localhost and  create /user/wce/input directory in HDFS
```$ ssh localhost```  
```$ hadoop fs -mkdir /user/wce/input```

![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/8creatingdirs.png)

7. Copy sample.txt file to the HDFS /user/wce/input/ directory.  
```$ hadoop fs -put sample.txt /user/wce/input```  
  
![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/9aftecopy.png)

8. Run the Map/Reduce job using command.  
 ```$ mapred streaming -file mapper.py -mapper mapper.py -file reducer.py -reducer reducer.py -input /user/wce/input/sample.txt -output /user/wce/output```  
![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/10maprrun.png)
 
9. The job is now running.  
![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/11mprrun.png)

10. View the results.  
```hadoop fs -ls /user/wce/output```  
```hadoop fs -cat /user/wce/output/*```  

![](https://github.com/AdityaSinghRathore/WordCountHadoop/blob/master/img/13finalresult.png)
 



