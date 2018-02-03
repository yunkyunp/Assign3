# Assign3
## Spring 2018

### 1
`
yunkyunp@trgn510:~/bin ls \| pointless.sh
POINTLESS.SH
`

#!/bin/bash
echo $VARIABLE
VARIABLE=5
echo $USER  # prints name of user
echo $VARIABLE #prints 5
VARIABLE=6
echo $VARIABLE #prints 6

### 2
`
yunkyunp@trgn510:~/bin ls \| quotequotes.sh
QUOTEQUOTES.SH
`

echo $HOSTNAME
VARIABLE="I am on $HOSTNAME"
echo VARIABLE # prints VARIABLE
echo $VARIABLE # prints I am on trgn510.pmed.io
VARIABLE='I am on $HOSTNAME'
echo $VARIABLE # prints I am on $HOSTNAME
VARIABLE="I am on \$HOSTNAME"
echo $VARIABLE #prints I am on $HOSTNAME
VARIABLE="The process id for this script is $$"
echo $VARIABLE

### 3
`
yunkyunp@trgn510:~/bin ls \| processes.sh
PROCESSES.SH
`
#!/bin/bash
myvar=$(ps -ax -u --sort pcpu | grep $USER | tail -n 5)
echo $myvar

### 4
`
yunkyunp@trgn510:~/bin ls \| makelower.sh
MAKELOWER.SH
`
#!/bin/bash
cat /dev/stdin | tr A-Z a-z 

### 5
`
yunkyunp@trgn510:~/bin ls \| add.sh
ADD.SH
`
#!/bin/bash
let results=0;
echo "First number:"
read num1
echo "Second number:"
read num2
let sum=$num1+$num2
echo $sum

### 7
`
yunkyunp@trgn510:~/bin ls \| count_by_to.sh
COUNT_BY_TO.SH
`
#!/bin/bash
echo "Starting number:"
read num1
echo "Last number:"
read num2

while [ $num1 -le $num2 ]
do
    echo $num1
    let num1=$num1+2
done
echo All done

### 9
`
yunkyunp@trgn510:~/bin ls \| whatgene.sh
WHATGENE.SH
`
#!/bin/bash
print_gene () {
    echo $Gene | tr a-z A-Z
    return 1
}
echo "Gene name:"
read Gene
print_gene $Gene

### 10
`
yunkyunp@trgn510:~/bin ls \| genotype.sh
GENOTYPE.SH
`
#!/bin/bash
grep -v "#" ~/projects/assign2/HG001_GRCh37_GIAB_highconf_CG-IllFB-IllGATKHC-Ion-10X-SOLID_CHROM1-X_v.3.3.2_highconf_PGandRTGphasetransfer.vcf | cut -d "       " -f 10 | cut -d ":" -f 1 > temp_genotype
grep -v "#" ~/projects/assign2/HG001_GRCh37_GIAB_highconf_CG-IllFB-IllGATKHC-Ion-10X-SOLID_CHROM1-X_v.3.3.2_highconf_PGandRTGphasetransfer.vcf | cut -d "       " -f1,2,4,5 > temp
paste temp temp_genotype > temp_output.txt
cat temp_output.txt | tr "      " " " > output.txt
head output.txt

