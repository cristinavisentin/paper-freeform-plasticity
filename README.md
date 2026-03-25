# paper-freeform-plasticity

Software artifacts for the experiments on the free-form plasticity mechanism for neural networks.

## How to reproduce the experiments

### Requirements
- JDK 25

These experiments are based on the evolutionary framework [JGEA](https://github.com/ericmedvet/jgea).

### XOR problem with me

```
java \
  -jar jgea.jar \
  -nt 92 -nr 4 \
  -f exp-files/booleans/mopm.txt \
  --expHeadLines \
    '$nOfEvals = 50000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```