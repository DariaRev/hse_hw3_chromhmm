## Домашнее задание 
### [Ссылка на колаб](https://colab.research.google.com/drive/1etXT_whG1EhZW5hORFJHBDydO_JTZLEA?usp=sharing)
---
Во втором домашнем задании рассматривалась клеточная линия IMR-90, но к сожалению она не содержит ChIP-Seq эксперименты в предложенных гистоновых метках. Поэтому для анализа будет рассматриваться клеточная линия K562.

## Таблица с гистоновыми метками

| Гистоновая метка      | Файл             |
| ------------- |:------------------:| 
| H2az     | H2azStdAlnRep1.bam    | 
| H3k27ac  | H3k27acStdAlnRep1.bam |  
| H3k27me3  | H3k27me3StdAlnRep1.bam |  
| H3k4me1	  | H3k4me1StdAlnRep1.bam  |  
| H3k4me2  | H3k4me2StdAlnRep1.bam |  
| H3k4me3  | H3k4me3StdAlnRep1.bam |  
| H3k79me2  | H3k79me2StdAlnRep1.bam |  
| H3k9me1  | H3k9me1StdAlnRep1.bam |  
| H3k9me3  | H3k9me3StdAlnRep1.bam |  
| H4k20me1  | H4k20me1StdAlnRep1.bam |  


## Картинки из выдачи ChromHMM

![emissions_10](https://user-images.githubusercontent.com/32986053/160289271-c43e99aa-f960-4ecd-9029-ff605b9680c2.png)
![transitions_10](https://user-images.githubusercontent.com/32986053/160289324-f28328ab-6b5b-4234-a079-45ff4379145b.png)
![K562_10_overlap](https://user-images.githubusercontent.com/32986053/160289290-e57dc54b-e2aa-4a94-a698-5345622b9646.png)

![K562_10_RefSeqTSS_neighborhood](https://user-images.githubusercontent.com/32986053/160289333-25b99463-14e9-4859-a18e-6b9b46bf6fe6.png)
![K562_10_RefSeqTES_neighborhood](https://user-images.githubusercontent.com/32986053/160289338-446da5ed-569b-420f-bb37-e973501036b2.png)

## Таблица состояний
| Состояние      | Характерные метки             | Название | Свойства  | Изображения |
| ------------- |:------------------:|:------------------:|:------------------:|:------------------:|
|  1    |  H3k27me3   | Transcribed | Находится и в интронах, и в экзонах| ![Снимок экрана 2022-03-27 в 20 31 59](https://user-images.githubusercontent.com/32986053/160296266-e4022c09-4c7a-45c2-b3e7-187341c18b74.png)|
|  2    |  H3k27me3   | Transcriptional elongation | Низкий сигнал, большой процент во всем геноме, обычно на интронах, но часто встречается на экзонах| ![Снимок экрана 2022-03-27 в 21 13 46](https://user-images.githubusercontent.com/32986053/160296277-c5ad5db8-7c86-489d-ba81-1bd729fe8ad5.png) |
|  3    |  -   | Heterochromatin |Большой процент находится в lamina, вообще большой процент во всем геноме, плюс находится в начале гена |![Снимок экрана 2022-03-27 в 21 21 13](https://user-images.githubusercontent.com/32986053/160296293-b7e5dffa-de26-46dd-99e1-9d58bbb159ca.png) |
|  4    |  H3k4me1, H2az   | Inactive promoter | Сигнал средний, находится обычно в интронах |![Снимок экрана 2022-03-27 в 21 15 15](https://user-images.githubusercontent.com/32986053/160296321-7ba55117-0d1c-45ba-87e5-02dcae2e25b2.png)|
|  5    |    H2az, H3k4me1, H3k4me2, H3k4me3, H3k27ac   | Promoter | сигнал средний, часто находится на интронах или вне гена|![Снимок экрана 2022-03-27 в 21 30 33](https://user-images.githubusercontent.com/32986053/160296327-d82c1684-e759-4d40-8a9f-97d815f6170f.png)|
|  6    |  H2az, H3k4me1   | Enhancer |Сигнал сильный, часто вне гена |![Снимок экрана 2022-03-27 в 21 26 23](https://user-images.githubusercontent.com/32986053/160296341-9de3b517-223b-401c-9c6b-8d3fce1dd8ac.png)|
|  7    | H2az, H3k4me2, H3k4me3, H3k27ac   | Insulator |Часто находится в CPG островках, довольно сильный сигнал, часто находится в интронах |![Снимок экрана 2022-03-27 в 21 18 29](https://user-images.githubusercontent.com/32986053/160296350-8ab8f02f-06f3-42ae-8fd1-c510f16afceb.png)|
|  8    |  H2az, H3k4me1, H3k4me2, H3k4me3, H3k27ac, H3k79me2  | Active promoter |Высокий сигнал, довольно большой процент в CPG островах, иногда на экзонах |![Снимок экрана 2022-03-27 в 21 41 45](https://user-images.githubusercontent.com/32986053/160296364-4a8dea2c-4829-47a0-9309-eee3e1aedfe1.png)|
|  9    |  H3k4me1, H3k4me2, H3k4me3, H3k79me2, H4k20me1   | Insulator | Часто перед промотером, сигнал средний, расположен в интронах |![Снимок экрана 2022-03-27 в 21 17 32](https://user-images.githubusercontent.com/32986053/160296380-35120c1d-310c-42c2-81d9-fd788bb044e9.png)|
|  10    | H3k79me2    | Inactive promoter | Сигнал средний, расположен в интронах  |![Снимок экрана 2022-03-27 в 21 34 15](https://user-images.githubusercontent.com/32986053/160296367-6bd90ff1-2a3a-4402-8a7c-fbf1be341bb6.png)|

##  Команды из колаба
```
!curl -O https://raw.githubusercontent.com/deepjavalibrary/d2l-java/master/tools/fix-colab-gpu.sh && bash fix-colab-gpu.sh
!curl -O https://raw.githubusercontent.com/deepjavalibrary/d2l-java/master/tools/colab_build.sh && bash colab_build.sh
!java --list-modules | grep "jdk.jshell"
! wget http://compbio.mit.edu/ChromHMM/ChromHMM.zip
!unzip /content/ChromHMM.zip
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H2azStdAlnRep1.bam -O H2az.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k27acStdAlnRep1.bam -O H3k27ac.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k27me3StdAlnRep1.bam -O H3k27me3.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k4me1StdAlnRep1.bam -O H3k4me1.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k4me2StdAlnRep1.bam -O H3k4me2.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k4me3StdAlnRep1.bam -O H3k4me3.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k9me1StdAlnRep1.bam -O H3k9me1.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k9me3StdAlnRep1.bam -O H3k9me3.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H4k20me1StdAlnRep1.bam -O H4k20me1.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562H3k79me2StdAlnRep1.bam -O H3k79me2.bam
! wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneK562ControlStdAlnRep1.bam -O control.bam
!java -mx5000M -jar /content/ChromHMM/ChromHMM.jar BinarizeBam -b 200  /content/ChromHMM/CHROMSIZES/hg19.txt /content/ cellmarkfiletable.txt   binarizedData
!java -mx5000M -jar /content/ChromHMM/ChromHMM.jar LearnModel /content/binarizedData output 10 hg19
!zip -r output.zip output
from google.colab import files
files.download("output.zip")
```

## [Бонусная часть](https://colab.research.google.com/drive/1GG26xYsxCLUwMHKiCrev3_xQ3FKfb9tF?usp=sharing)

```
names = ['Transcribed','Transcriptional_elongation', 'Heterochromatin', 'Inactive_promoter', 'Promoter', 'Enhancer', 'Insulator', 'Active_promoter', 'Insulator', 'Inactive_promoter']
with open(f'K562_10_expanded.bed', 'r') as r:
    with open(f'K562_10_expanded_new2.bed', 'a') as w:
        for line in r.readlines():
            if 'track' in line or 'browser' in line :
                w.write(line)
            else:
                spli = line.split('\t')
                spli[3] = names[int(spli[3])-1]
                w.write('\t'.join(spli))
```
![Снимок экрана 2022-03-28 в 00 44 34](https://user-images.githubusercontent.com/32986053/160302534-4d55868a-e01a-4c6c-b2fc-a54b92994941.png)
![Снимок экрана 2022-03-28 в 00 47 58](https://user-images.githubusercontent.com/32986053/160302541-d167f21f-e84a-4631-93ae-0a19f95ea834.png)
