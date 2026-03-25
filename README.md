# paper-freeform-plasticity

Software artifacts for the experiments on the free-form plasticity mechanism for neural networks.

## How to reproduce the experiments

### Requirements
- JDK 25

These experiments are based on the evolutionary framework [JGEA](https://github.com/ericmedvet/jgea).

### Experiments
All the following experiments compare (unless otherwise specified) four plasticity laws evolved the with MAP-Elites algorithm.
These four plasticity laws are:
- Free-form plasticity 
- Four variants of the ABCD-Hebbian learning (Synape-, Neuron-, Layer-, Network-ABCD)

#### Experiment: the xor task
```
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
```
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
```
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
```
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
```
java \
  -jar jgea.jar \
  -nt 92 -nr 10 \
  -f exp-files/booleans/parity.txt \
  --expHeadLines \
    '$nOfEvals = 50000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```