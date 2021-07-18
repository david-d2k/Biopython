
![biopythonlogo](http://biopython.org/DIST/docs/tutorial/images/biopython_logo.svg)

## <span style="color:blue">O que é Biopython?</span>
#### <span style="color:black">Biopython é uma biblioteca ou uma suite de ferramentas,  escritas em Python para manipulação de dados biológicos disponível gratuitamente. Desenvolvida pelo Projeto Biopython (http://www.biopython.org), onde no seu site, é fornecido recursos online para módulos, scripts e links da web para desenvolvedores de software baseado em Python para uso e pesquisa em bioinformática.</span>

## <span style="color:blue">Seu objetivo</span>
#### <span style="color:black"> Basicamente, o objetivo do Biopython é facilitar ao máximo o uso do Python para bioinformática, criando módulos e classes reutilizáveis ​​de alta qualidade.</span>

 ## <span style="color:blue">Recursos</span>
 #### <span style="color:black">Os recursos do Biopython incluem analisadores para vários formatos de arquivo de bioinformática (BLAST, Clustalw, FASTA, Genbank, ...), acesso a serviços online (NCBI, Expasy, ...), interfaces para programas comuns e não tão comuns (Clustalw, DSSP, MSMS ...), uma classe de sequência padrão, vários módulos de agrupamento, uma estrutura de dados em árvore KD etc; e até mesmo documentação.
</span>

## <span style="color:blue">Exemplos de aplicação:</span>

### <span style="color:blue">1 - Trabalhando com sequências:</span>
#### <span style="color:black">O objeto central em bioinformática é a sequência. Assim, começaremos com uma introdução rápida aos mecanismos Biopython para lidar com sequências, o objeto (Seq).</span>



```python
# Veja que para utilizar a biblioteca biopython, primeiro temos que instalá-la
!pip3 install biopython
```

    Requirement already satisfied: biopython in /home/d2k/anaconda3/lib/python3.8/site-packages (1.79)
    Requirement already satisfied: numpy in /home/d2k/anaconda3/lib/python3.8/site-packages (from biopython) (1.20.1)



```python
# Por enquanto para tratar com sequências, precisaremos importar apenas a ferramenta
# (Seq) da biblioteca biopython
from Bio.Seq import Seq
# Agora criaremos uma variável (minha_sequencia) para receber a sequência especificada
minha_sequencia = Seq('AGTACACTGGT')
print('Minha sequência é:', minha_sequencia)

```

    Minha sequência é: AGTACACTGGT



```python
# Agora vamos mostrar a sequência complementar da amostra (AGTACACTGGT)
# Adenina (A) <-> Timina (T) ; Guanina (G) <-> Citosina (C)
print('Minha sequência complementar é:', minha_sequencia.complement())

```

    Minha sequência complementar é: TCATGTGACCA



```python
# Agora a sequência reversa da complementar (TCATGTGACCA)
print('Minha sequência reversa complementar é:', minha_sequencia.reverse_complement())

```

    Minha sequência reversa complementar é: ACCAGTGTACT



```python
# Analise de quantos nucleotídeos possui cada amostra do arquivo West_Nile_virus.fa
# Observação: É preciso baixar o arquivo em sua máquina e mostrar o caminho até ele
from Bio import SeqIO
for seq_record in SeqIO.parse("/home/d2k/Documents/biopython/Teste/West_Nile_virus.fa", "fasta"):
    print(seq_record.id)
    print(repr(seq_record.seq))
    print(len(seq_record))
    
```

    JN591737
    Seq('GTGGATTTGGTTCTCGAAGGCGACAGCTGTGTGACCATCATGTCTAAGGACAAG...ACC')
    202
    AY944238
    Seq('CTGATCGACGGCAAGGGACCAATACGATTCGTGTTGGCTCTCTTGGCGTTCTTC...CTG')
    921
    KF437832
    Seq('GGCCTTCATACACACTAAAGCTTGGAGAGTATGGAGAGGTGACAGTGGACTGTG...GGA')
    250
    KJ433825
    Seq('TGCGGGGTGCCTTCATACACACTAAAGCTTGGAGAGTATGGAGAGGTGACAGTG...TGG')
    256



```python
# Saber quantos nucleotídeos existe na amostra do Ebola
from Bio import SeqIO
from Bio.SeqUtils import GC
for seq_record in SeqIO.parse("/home/d2k/Documents/biopython/Teste/Sudan_ebolavirus_isolate_IRF0154_partial_genome.fa", "fasta"):
    print(seq_record.id)
    print(repr(seq_record.seq))
    print('Total de nucleotídeos na amostra:', len(seq_record))
    
```

    KY425644
    Seq('TTTTTTATACTTTTTGTGTGCGAATAACTATGAGGAAGATTAATCATTTTCCTC...CTC')
    Total de nucleotídeos na amostra: 18836



```python
from Bio.Seq import Seq
from Bio.SeqUtils import GC
my_seq = Seq('TTTTTTATACTTTTTGTGTGCGAATAACTATGAGGAAGATTAATCATTTTCCTCAAACTCAAACTAATAT')
print('Total de nucleotídeos na amostra:', len(my_seq))
print("Total de Adenina ->", my_seq.count("A"))
print("Total de Timina ->", my_seq.count("T"))
print("Total de Guanina ->", my_seq.count("G"))
print("Total de Citosina ->", my_seq.count("C"))
print("Porcentagem de GC ->",GC(my_seq),"%")

```

    Total de nucleotídeos na amostra: 70
    Total de Adenina -> 23
    Total de Timina -> 29
    Total de Guanina -> 8
    Total de Citosina -> 10
    Porcentagem de GC -> 25.714285714285715 %


## <span style="color:blue">Tecnologia utilizadas:</span>
<span style="color:black">Sistema Operacional Fedora 34, Anaconda, Jupyter Notebook</span>



## <span style="color:blue">Para saber mais:</span>
   http://biopython.org/DIST/docs/tutorial/Tutorial.html#sec3
