# hse_hw1_meth
Collab: https://colab.research.google.com/drive/1LuHgZJweH2GRWw2Qy14VJcqPBJnHaf_w?usp=sharing
.
Интересное распределение GC-состава, а также его значение (26% для SRR5836475_1.fastq, в то время как норма ~50% или чуть меньше). В норме C~=G~=A~=T, в то время как в данных бисульфитного секвенирования С~=10%, T~=40%. То есть то, что мы наблюдаем - артефакт бисульфитного секвенирования, ведь большая часть цитозина неметилирована, поэтому из-за бисульфита превращается в урацил, который считывается как тимин. 
![image](https://user-images.githubusercontent.com/60808830/154700376-697c479e-9107-4455-adea-62f3243520e0.png)
![image](https://user-images.githubusercontent.com/60808830/154698221-dc936096-cd15-44d9-b431-e0e501d13568.png)
![image](https://user-images.githubusercontent.com/60808830/154698840-6f2c7965-8cc3-421f-aa62-1eb9cb473c41.png)
.
Bismark Report можно найти в файлах.
![image](https://user-images.githubusercontent.com/60808830/154701705-63ef7923-974b-47db-b90b-cb808b90ac54.png)
![image](https://user-images.githubusercontent.com/60808830/154701150-d204f459-1106-49c3-a891-9735e81fcb6d.png)
