# paper-freeform-plasticity
This repository contains the software artifacts and experiment configurations used in the study on **free-form plasticity mechanisms for neural networks**.

It allows you to reproduce the experimental results presented in the paper, including all reported figures.


## How to reproduce the experiments
### Requirements
- JDK 25
- Maven 
- Git

### Setup
#### 1. Clone this repository
```bash
git clone https://github.com/cristinavisentin/paper-freeform-plasticity.git                      
```
#### 2. Build the JGEA framework
These experiments rely on [JGEA](https://github.com/ericmedvet/jgea), an evolutionary computation framework used to run optimization experiments.
Since the executable JAR is not provided here, you must build it from source:
```bash
git clone https://github.com/ericmedvet/jgea.git
cd jgea
git checkout develop
mvn clean package -U
```

#### 3. Link the executable
Copy the generated JAR file into your experiment directory:
```bash
cd ../paper-freeform-plasticity
cp ../jgea/io.github.ericmedvet.jgea.experimenter/target/jgea.experimenter-2.8.2-SNAPSHOT-jar-with-dependencies.jar jgea.jar                       
```

## Experiments
The experiments compare **free-form plasticity** against four variants of **ABCD-Hebbian learning** (Synapse-, Neuron-, Layer-, and Network-ABCD) evolved using the **MAP-Elites** algorithm (unless otherwise specified). 

The default neural network is a multilayer perceptron (MLP) with architecture: $l=(2, 2, 1)$.

> **!** Replace `<threads>` in the commands below with a number suitable for your machine (e.g., `-nt 8`).

### Boolean tasks
#### 1. The XOR task
To reproduce the results shown in **Figure 1**, **Figure 2** and **Figure 3** of the paper, run the following command:
```bash 
java \
  -jar jgea.jar \
  -nt <threads> \
  -f exp-files/booleans/xor.txt \
  --expHeadLines \
    '$nOfEvals = 25000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```
#### 2. Testing different topologies on the XOR task
You can run the experiment with different network structures, as shown in **Figure 4** of the paper, by modifying the `$innerLayers` parameter:
- Wide architecture $l=(2, 8, 1)$: set `$innerLayers = [8]`;
- Deep architecture $l=(2, 2, 2, 1)$: set `$innerLayers = [2; 2]`.


#### 3. Plasticity evolved through genetic algorithm (GA) on the XOR task
To run the XOR task using a standard GA instead of MAP-Elites, as shown in **Figure 5** of the paper:
```bash
java \
  -jar jgea.jar \
  -nt <threads> \
  -f exp-files/booleans/xor-ga.txt \
  --expHeadLines \
    '$nOfEvals = 25000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

#### 4. The MOPM-3 task
```bash
java \
  -jar jgea.jar \
  -nt <threads> \
  -f exp-files/booleans/mopm.txt \
  --expHeadLines \
    '$nOfEvals = 50000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

#### 5. The even parity-5 task
```bash
java \
  -jar jgea.jar \
  -nt <threads> \
  -f exp-files/booleans/parity.txt \
  --expHeadLines \
    '$nOfEvals = 50000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

### 2D navigation task
todo 

## More experiments (not shown in the paper)
#### The free-form modulable expressiveness (on the XOR task)
```bash
java \
  -jar jgea.jar \
  -nt <threads> \
  -f exp-files/booleans/xor-building-blocks.txt \
  --expHeadLines \
    '$nOfEvals = 25000' \
    '$seeds = [1:1:30]' \
    '$innerLayers = [2]'
```

## Notes
- Results (plots and logs) are generated in the `results` directory.
- Execution time may vary depending on the number of threads and seeds.