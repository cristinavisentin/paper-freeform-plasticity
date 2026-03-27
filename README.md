# paper-freeform-plasticity

Software artifacts for the experiments on the free-form plasticity mechanism for neural networks.

## How to reproduce the experiments

### Requirements
- JDK 25
- Maven 

These experiments are based on the evolutionary framework [JGEA](https://github.com/ericmedvet/jgea).

Clone this repository to access the experiment files:
```bash
git clone https://github.com/cristinavisentin/paper-freeform-plasticity.git                      
```
In oderer to execute them, the executable file `.jar` is needed. To obtain it, clone and build JGEA with the following commands:
```bash
git clone https://github.com/ericmedvet/jgea.git
cd jgea
git checkout develop
mvn clean package -U
```
Then locate in the `paper-freeform-plasticity` direcotory and copy the `.jar`:
```bash
cd paper-freeform-plasticity
cp ../jgea/io.github.ericmedvet.jgea.experimenter/target/jgea.experimenter-2.8.2-SNAPSHOT-jar-with-dependencies.jar jgea.jar                       
```

### Experiments
All the following experiments compare (unless otherwise specified) four plasticity laws evolved the with MAP-Elites algorithm.
These four plasticity laws are:
- Free-form plasticity 
- Four variants of the ABCD-Hebbian learning (Synape-, Neuron-, Layer-, Network-ABCD)

#### Experiment: the xor task
```bash 
java \
  -jar jgea.jar \
  -nt 92 -nr 10 \
  -f exp-files/booleans/xor.txt \
  --expHeadLines \
    '$nOfEvals = 25000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```
To try with different network topologies just vary the command line parameter `$innerLayers`, we experimented with `$innerLayers = [8]` and `$innerLayers = [2; 2]`.

#### Experiment: investigation on free-form expressiveness (on the xor task)
```bash
java \
  -jar jgea.jar \
  -nt 92 -nr 10 \
  -f exp-files/booleans/xor-building-blocks.txt \
  --expHeadLines \
    '$nOfEvals = 25000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

#### Experiment: the xor task with genetic algorithm (GA)
```bash
java \
  -jar jgea.jar \
  -nt 92 -nr 10 \
  -f exp-files/booleans/xor-ga.txt \
  --expHeadLines \
    '$nOfEvals = 25000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

#### Experiment: the mopm-3 task
```bash
java \
  -jar jgea.jar \
  -nt 92 -nr 10 \
  -f exp-files/booleans/mopm.txt \
  --expHeadLines \
    '$nOfEvals = 50000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

#### Experiment: the parity-5 task
```bash
java \
  -jar jgea.jar \
  -nt 92 -nr 10 \
  -f exp-files/booleans/parity.txt \
  --expHeadLines \
    '$nOfEvals = 50000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```