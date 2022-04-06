# Chhh
| ![image](https://user-images.githubusercontent.com/60808830/161844282-b5ee858a-deb4-4dcf-8cca-6795ff093531.png) | ![image](https://user-images.githubusercontent.com/60808830/161844351-f562097b-ad49-4781-aed7-ecd9c46bdd04.png) | ![image](https://user-images.githubusercontent.com/60808830/161844429-8344a8ec-625f-4bb4-b425-5cec8280dc36.png) | ![image](https://user-images.githubusercontent.com/60808830/161844478-41ce1bc4-09dc-400d-a5ce-dcd20cb9ccf7.png) | ![image](https://user-images.githubusercontent.com/60808830/161844514-0c4238b1-d98a-471f-912b-ae88bc89bd72.png) |
| ------------- | ------------- |--------------------| -- | -- |


**анализ**
|![image](https://user-images.githubusercontent.com/60808830/161910628-6aa60a02-77aa-4a63-bf84-c4de56606273.png) | ![image](https://user-images.githubusercontent.com/60808830/161845100-05a7ddec-cd74-4427-93d4-55081712d738.png)  | !![image](https://user-images.githubusercontent.com/60808830/161845182-8f76f3c5-4fed-40c9-be3b-59518bd36ede.png) | ![image](https://user-images.githubusercontent.com/60808830/161845182-8f76f3c5-4fed-40c9-be3b-59518bd36ede.png) | ![image](https://user-images.githubusercontent.com/60808830/161845182-8f76f3c5-4fed-40c9-be3b-59518bd36ede.png) |
| ------------- | ------------- |--------------------| -- | -- |

**выводы**
1,6 (Большой процент RefSeqGene.),7(нет меток), 9(нет меток)- транскрибируется \t
2, 4, 5 - энхансер (H3k4me1StdAlnRep1.bam, H3k4me2StdAlnRep1.bam, H3k27acStdAlnRep1.bam) \t
3(нет меток), 8 - промотер \t
10(нет меток) -гетерохроматин \t

![image](https://user-images.githubusercontent.com/60808830/161910628-6aa60a02-77aa-4a63-bf84-c4de56606273.png)
**Бонус**
![image](https://user-images.githubusercontent.com/60808830/161913262-86d349db-c5b9-4386-bdae-fd40674f3c62.png)


! zip -r model_output.zip LearnModelOut/
AR = ['Transcribed', 'Enhancer', 'Promoter', 'Enhancer', 'Enhancer', 'Transcribed', 'Transcribed',
                'Promoter', 'Transcribed', 'Heterochromatin']
with open(f'/content/HeLa-S3_10_expanded.bed', 'r') as file1:
    with open(f'/content/result.bed', 'a') as file2:
        n = file1.readlines()
        for i in n:
            if i[:5] == 'track' or i[:5] == 'brows':
                file2.write(i)
            else:
                splitted_i = i.split('\t')
                idx = int(splitted_i[3])
                splitted_i[3] = splitted_i[3]+"_" + analysis_res[idx-1]
                file2.write('\t'.join(splitted_i))
