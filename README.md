# hse24_hw3
В данной работе я продолжила рассматривать клеточную линию K562

| Клеточная линия | Имя в табличке | Файл |
| - | - | - |
|K562 |H2az |wgEncodeBroadHistoneK562H2azStdAlnRep1.bam |
|K562 |H3k27ac |wgEncodeBroadHistoneK562H3k27acStdAlnRep1.bam
|K562 |H3k27me3 |wgEncodeBroadHistoneK562H3k27me3StdAlnRep1.bam | 
|K562 |H3k36me3 |wgEncodeBroadHistoneK562H3k36me3StdAlnRep1.bam |
|K562 |H3k4me1 |wgEncodeBroadHistoneK562H3k4me1StdAlnRep1.bam | 
|K562 |H3k4me2 |wgEncodeBroadHistoneK562H3k4me2StdAlnRep1.bam | 
|K562 |H3k4me3 |wgEncodeBroadHistoneK562H3k4me3StdAlnRep1.bam | 
|K562 |H3k79me2 |wgEncodeBroadHistoneK562H3k79me2StdAlnRep1.bam | 
|K562 |H3k9ac |wgEncodeBroadHistoneK562H3k9acStdAlnRep1.bam | 
|K562 |H3k9me1 |wgEncodeBroadHistoneK562H3k9me1StdAlnRep1.bam | 

|Клеточная линия | Файл контроля |
| - | - |
| K562 | wgEncodeBroadHistoneK562ControlStdAlnRep1.bam |

## ChromHMM

Файл cellmarkfiletable.txt был создан вручную по мануалу. 

Результаты работы [нотбука](https://colab.research.google.com/drive/1ad7zThEya2KaeNOx7Pk0lJNzhnGi-qsM?usp=sharing) лежат в папке data.
| Emission parametrs | Transition parameters | Fold Enrichment K562|
| - | - | - |
| ![image](https://github.com/prayforanya/hse24_hw3/blob/main/data/emissions_10.png) |![image](https://github.com/prayforanya/hse24_hw3/blob/main/data/transitions_10.png) | ![image](https://github.com/prayforanya/hse24_hw3/blob/main/data/K562_10_overlap.png)|

Custom track был настроен с помощью bed-файла dense.bed. Были добавлены треки CpG островков и laminB1lads. Результаты по трем разным участкам 10 хромосомы лежат в файлах ucsc_1.pdf, ucsc_2.pdf, ucsc_3.pdf в папке data.

На основе результатов ChroHMM и геномному браузеру, а также [статье](https://static-content.springer.com/esm/art%3A10.1038%2Fnbt.1662/MediaObjects/41587_2010_BFnbt1662_MOESM5_ESM.pdf), мной были сделаны следующие предположения.

| Состояние | Название | Расположение | Метки |
| - | - | - | - |
| 1 | heterochromatin |  laminB1lads и RefSeqTES  | H3K27me3(вероятность мала) |
| 2 | ﻿unmappable | laminB1lads | -  |
| 3 | transcriptional elongation  | RefSeqTES, RefSeqGene и RefSeqExon | H3k36me3 (вероятность мала) |
| 4 | transcriptional transition | RefSeqGene | H3k79me2 |
| 5 | strong enhancer  |  RefSeqTES и RefSeqGene | H3k79me2 и H3k4me1 |
| 6 | weak promoter| RefSeqTES | H3k4me1|
| 7 | strong enhancer | RefSeqTES и RefSeqExon | H3k4me1, H3k27ac и H2az |
| 8 | weak enhancer | laminB1lads | H3k4me1 и H2az 
| 9 | active promoter | CpGIslands, RefSeqExon, RefSeqTES, RefSeqTSS и RefSeqTSS2kb | H3k9ac, H3k4me2, H3k4me3 и H2az|
| 10 | active promoter  | RefSeqExon, RefSeqTES и RefSeqTSS2kb | H3K27ac, H3k9ac, H3k4me2 и H3k4me3 |

## Бонус

Вручную поправила файл K562_10_dense.bed в TextEdit с помощью команды cntrl+f. Новый файл весит больше 25Мб, поэтому его пришлось заархивировать. Новый файл лежит в папке data под названием upadate_dense.bed.zip. Визуализация в геномном браузере разных участков лежат в файлах updated_ucsc_1.pdf, updated_ucsc_2.pdf, updated_ucsc_3.pdf в папке data.
