
## Ejercicios VCF Tools

#####Hacer un contenedor de vcftools

```
vcftools="docker run --rm -v /home/san/Desktop/BioinfinvRepro/Unidad5/Prac_Uni5/wolves.vcf:/data biocontainers/vcftools:0.1.15 vcftools"
```

#####a) ¿Cuántos individuos y variantes (SNPs) tiene el archivo?
```
$vcftools --vcf wolves.vcf 
```
#####b) Calcula la frecuencia de cada alelo para todos los individuos dentro del archivo y guarda el resultado en un archivo.
```
$vcftools --vcf wolves.vcf --out wolves_freq --freq
```
#####c) ¿Cuántos sitios del archivo no tienen missing data?
```
$vcftools --vcf wolves.vcf --max-missing 1
```
#####d) Calcula la frecuencia de cada alelo para todos los individuos pero solo para los sitios sin missing data y guarda el resultado en un archivo.
```
$vcftools --vcf wolves.vcf --out wolves_frequency_nomiss --max-missing 1 --freq
```
#####e) ¿Cuántos sitios tienen una frecuencia del alelo menor \<0.05?
```
$vcftools --vcf wolves.vcf --out maf --max-maf 0.05 --freq
```
#####f) Calcula la heterozygosidad de cada individuo.
```
$vcftools --vcf wolves.vcf --het --out wolves_het
```
#####g) Calcula la diversidad nucleotídica por sitio.
```
$vcftools --vcf wolves.vcf --site-pi --out div_nuc
```
##### h) Calcula la diversidad nucleotídica por sitio solo para los sitios del cromosoma 3
```
$vcftools --vcf wolves.vcf --site-pi --chr chr03 --out div_nuc_chr3
```
#####i) Filtra los sitios que tengan una frecuencia del alelo menor \<0.05 y crea un archivo nuevo llamado wolves_maf05.vcf.
```
$vcftools --vcf wolves.vcf --maf 0.05 --recode
mv out.recode.vcf wolves_maf05.vcf
```
#####j) Convierte el archivo wolves_maf05.vcf a formato plink.
```
$vcftools --vcf wolves_maf05.vcf  --plink --out wolves_maf05
```

