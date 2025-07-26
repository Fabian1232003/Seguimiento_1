# Analisis  Bioinformatico Calidris pugnax

### Que es un archivo .gff

Este archivo es un formato usado en bioinformatica que consiste de nueve columnas separadas por tabs la primera columna contienen 

- Nombre, puede ser de la secuencia de el cromosoma del gen etc
- Fuente , de donde se sacaron los datos (NCBI, Genebank, etc.)
- Tipo, si es un CDS, exon, intron ORF etc.
- Comienzo de la secuencia, esto es un numero y habla de la ubicacion de esta 
- Final de la secuencia, de nuevo un numero
- Puntuacion, indicando la confiabilidad de la secuencia  
- Cadena de ADN si es la foward "+" o reverse "-"
- Phase, en caso de ser un gen te dice donde comenzar a leer las tripletas por ejemplo si es uno se comienza a leer el codon en el segundo nucleotido 
- Atributos, indica varias cosas como un id unico si la secuencia es hija de otro ente en el arcivo, si es ADN circular entre otras cosas 

### Calidris pugnax Datos 
- Es un ave limicola que habita en Eurasia y Africa, el ave presenta tamaño mediano y se alimenta de gusanos insectos y semillas 


### ¿Cuantos features contiene el archivo?
El archivo contiene 19 features ordenadas de mayor incidencia a menor incidencia 
<img src="image.png" alt="" width="600">

### ¿Cuantas regiones de la secuencia (cromosomas) contiene el archivo?
- Para contestar esto se tomo como "biological_region" la region del cromosoma tambien hay una region 1 se sospecha que la region biologica es una subdivision de la region 1, hay 52035 "biological_regions"
  
  ### ¿Cuántos genes están listados en el organismo?
- Solo se tomaron en cuenta la cantidad de entradas distintas del apartado "gene" ya que habia otras regiones que tenian la palabra gene incluidas pero son cosas como cdRNA_gene que se puede ver como hijo de la categoria gene, hay 16422 genes distintos, tambien se comprobo que cada linea de gen es unica haciendo extrallendo del archvivo cada gen con su respectivo id y comprobando que el numero sea igual al numero de lineas de la columna tres que dicen la palabra gen, se uso el siguiente codigo 

```bash
cut -f3,9 Ave.gff3 | grep -v "^#" | grep -i "^gene" | awk -F'\t' '{ match($2, /gene:([^;]+)/, arr); if(arr[1]!="") print arr[1] }' | sort | uniq | wc -l
```

### ¿Cuál es el top 10 de tipo de features (columna 3) más anotados en el genoma?
<img src="image-1.png" alt="" width="400">
