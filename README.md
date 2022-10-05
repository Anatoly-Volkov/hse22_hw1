**Создадим символические ссылки на файлы при помощи команд**

ln -s /usr/share/data-minor-bioinf/assembly/oil_R1.fastq

ln -s /usr/share/data-minor-bioinf/assembly/oil_R2.fastq

ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R1_001.fastq

ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R2_001.fastq

**Выберем из них случайные чтения**

seqtk sample -s306 oil_R1.fastq 5000000 > oil-pair1.fastq

seqtk sample -s306 oil_R1.fastq 5000000 > oil-pair2.fastq

seqtk sample -s306 oilMP_S4_L001_R1_001.fastq 1500000 > oil-mate1.fastq

seqtk sample -s306 oilMP_S4_L001_R1_001.fastq 1500000 > oil-mate2.fastq

**Оценим качество при помощи fastqc и multiqc**

fastqc oil-pair*

fastqc oil-maate*

multiqc .

Получим следующие результаты

![](img/report1.jpg)
![](img/report2.jpg)
![](img/report3.jpg)

**Теперь подрежем чтения при помощи platanus и еще раз оценим качество**

platanus_trim oil-pair1.fastq oil-pair2.fastq
platanus_internal_trim oil-mate1.fastq oil-mate2.fastq

![](img/report4.jpg)
![](img/report5.jpg)
![](img/report6.jpg)





