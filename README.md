# Assign3
## Spring 2018

The purpose of this exercise is to get comfortable creating scripts using vim on a server, while teaching you the remainder of bash scripting you'll need as a foundation for this course. The scripts themselves are not particularly exciting but they are the building blocks you'll need.  You will be asked to create 11 scripts, which all come from http://dtg.usc.edu/tgrn510/index.php/bash-scripting/.  These are to all be placed in your "bin" directory. The results of running these should be put into a forked version of this github. 

The final question is considerably more difficult and requires you to put concepts together you have learned at this point.

 Completion means the scripts work in your home directory and you have put the results in your github where you will replace the placeholder text with the results from running the script. For exampler, you should replace

*REPLACE WITH RESULTS*

with codeblock text using backticks, which show both the program being called in trgn510.pmed.io and the result.  After, it should be:

`
davidcraig@trgn510:~/bin ls \| test.sh
TEST.SH
`

### 1
Please create pointless.sh, changing from printing your hostname with $HOSTNAME, to your $USER

#!/bin/bash
echo $VARIABLE
VARIABLE=5
echo $USER  # prints name of user
echo $VARIABLE #prints 5
VARIABLE=6
echo $VARIABLE #prints 6

### 2
Please create quotequotes.sh, please add 1 additional lines that prints the process id of the current script using a special variable in a sentence: "The process id for this script is **235**'

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
Please create processes.sh.  Modify it such that it prints the top 5 CPU consuming processes

#!/bin/bash
myvar=$(ps -ax -u --sort pcpu | grep $USER | tail -n 5)
echo $myvar

### 4
Please create makeupper.sh.  Modify it to return lower case results, and change the name to makelower.sh

cat /dev/stdin | tr A-Z a-z 

### 5
Referring to math.sh, create a script called add.sh that takes two inputs and adds them, ** `add.sh 5 3` ** would print 8

#!/bin/bash
let results=0;
echo "First number:"
read num1
echo "Second number:"
read num2
let sum=$num1+$num2
echo $sum

### 6
Create a program "mb_or_kb.sh", referring to bigornot.sh and useful.sh, create a script called big file that checks to see if the file exists provided as the first argument exists, and if it exists then gets the filesize, storing it as a variable. I have not provided you with a way to get filesize in exercise, and expect you to search web for a way.  The program then checks to see if the size is greater than 1,000,000.  If its less then 1,000,000, it prints the number of kilobytes (divide by 1000) followed by "kB".  If its greater than 1,000,000, then print the number of megabytes followed by "MB".

*REPLACE WITH RESULTS for `mb_or_kb.sh ~/.bashrc` *

### 7
Create a program "count_by_to.sh", referring to count.sh.  The file should take two arguments, and should count jumping by the first argument until the second argument is reached, starting at 0.  For example, *count.sh 2 10* would print 0 2 4 6 8 10

#!/bin/bash
# Basic while loop
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
Please create whatgene.sh.  Please edit such that the function print_gene, prints upper case of the input.

#!/bin/bash
# Setting a return status for a function
print_gene () {
    echo $Gene | tr a-z A-Z
    return 1
}
echo "Gene name:"
read Gene
print_gene $Gene

### 10
Please create a bash shell called "genotype.sh" that takes a VCF as argument 1, and prints space delimited chromosome, position, reference, alternative, and genotype for all variants in the VCF.

#!/bin/bash
grep -v "#" ~/projects/assign2/HG001_GRCh37_GIAB_highconf_CG-IllFB-IllGATKHC-Ion-10X-SOLID_CHROM1-X_v.3.3.2_highconf_PGandRTGphasetransfer.vcf | cut -d "       " -f 10 | cut -d ":" -f 1 > temp_genotype
grep -v "#" ~/projects/assign2/HG001_GRCh37_GIAB_highconf_CG-IllFB-IllGATKHC-Ion-10X-SOLID_CHROM1-X_v.3.3.2_highconf_PGandRTGphasetransfer.vcf | cut -d "       " -f1,2,4,5 > temp
paste temp temp_genotype > temp_output.txt
cat temp_output.txt | tr "      " " " > output.txt
head output.txt

