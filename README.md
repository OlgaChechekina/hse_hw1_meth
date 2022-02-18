# hse_hw1_meth
Collab: https://colab.research.google.com/drive/1LuHgZJweH2GRWw2Qy14VJcqPBJnHaf_w?usp=sharing  

Интересное распределение GC-состава, а также его значение (26% для SRR5836475_1.fastq, в то время как норма ~50% или чуть меньше). В норме C~=G~=A~=T, в то время как в данных бисульфитного секвенирования С~=10%, T~=40%. То есть то, что мы наблюдаем - артефакт бисульфитного секвенирования, ведь большая часть цитозина неметилирована, поэтому из-за бисульфита превращается в урацил, который считывается как тимин.  

![image](https://user-images.githubusercontent.com/60808830/154700376-697c479e-9107-4455-adea-62f3243520e0.png)  

![image](https://user-images.githubusercontent.com/60808830/154698221-dc936096-cd15-44d9-b431-e0e501d13568.png)  

![image](https://user-images.githubusercontent.com/60808830/154698840-6f2c7965-8cc3-421f-aa62-1eb9cb473c41.png)  

Дедупликация:  
!ls *bt2_pe.bam | xargs -P 3 -tI{} deduplicate_bismark  --bam  --paired  -o {}.dedup  {}  
<img width="623" alt="summ" src="https://user-images.githubusercontent.com/60808830/154759570-88abf628-872d-4105-9304-55c3c0909d6d.PNG">


Bismark Report и M-bias plots можно найти в файлах.  

Из М-bias видно, что в данных epiblast высокий процент метилирования, в то время как в ICM высокий, что согласуется с данными статьи.  
Также заметно, что для обратных ридов обнаруживается меньший процент метилирования, вероятно это происходит в силу особенностей проведения реакции.  
<img width="844" alt="SRR73_bias_M_R1" src="https://user-images.githubusercontent.com/60808830/154758887-115ca684-dc23-495e-92e6-577a2db7bcd7.PNG">
<img width="832" alt="SRR73_bias_M_R2" src="https://user-images.githubusercontent.com/60808830/154758918-ce83d931-d412-4189-abdc-e8214ea554b0.PNG">  
Уровень покрытия, метилирования:  

! bedGraphToBigWig s_SRR5836473_1_bismark_bt2_pe.deduplicated.bedGraph m.chrom.sizes cell8_methylation.bigWig.bw  
! bedGraphToBigWig s_SRR3824222_1_bismark_bt2_pe.deduplicated.bedGraph m.chrom.sizes epiblast_methylation.bigWig.bw  
! bedGraphToBigWig s_SRR5836475_1_bismark_bt2_pe.deduplicated.bedGraph m.chrom.sizes icm_methylation.bigWig.bw  
! make_tracks_file --trackFiles cell8_methylation.bigWig.bw epiblast_methylation.bigWig.bw icm_methylation.bigWig.bw -o tracks.ini  
! pyGenomeTracks --tracks tracks.ini --region chr11:3000000-4000000 -o image.png  
<img width="959" alt="meth_cov" src="https://user-images.githubusercontent.com/60808830/154759029-3f43f2b1-378e-4a2e-92cc-8803ebc9d964.PNG">

