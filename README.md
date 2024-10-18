# cpuinfo

A python tool to list cpu(s) information.

[![asciicast](https://asciinema.org/a/FXa6HLpRjHbkSfxqykavedI0V.svg)](https://asciinema.org/a/FXa6HLpRjHbkSfxqykavedI0V)
## Features
- No 3rd party tools required
- Reads all information from virtual file systems `/proc` & `/sys`
- Produces a nice output formatted in yaml with almost all information found in all other tools in the market
- Numa information, including distances, memory usages per node and numa stats
- Better cpu flags description
- List of known Cpu Vulnerabilities with description
- Include current active CPU vulnerabilities (not found in any other tools)
- General Cpu characteristics
- Detailed and brief CPU cache memory information
- Detailed cpu cores information and which cpu(s) assigned to them taking into consideration hyperthreading

## Installation

```
pip install git+https://github.com/Hamdy/cpuinfo
```

## Usage
- `cpuinfo`
- Alternatively  to get better colorful yaml experience in shell
    ```
    sudo snap install yq
    cpuinfo | yq
    ```


## Motivation

Each tool in the market to list cpu information has some limitations and no one tool gives all information needed. 
`cpuinfo` tries to get the best out of all available tools in the market in one package that does not require any 3d party tools installation.
Here's a summary for pros & cons for these tools 

## Comparison between tools that displayes CPU(s) information

### `/proc/cpuinfo`
| Pros    | Cons |
| -------- | ------- |
| No 3rd party package is required  | Difficut to understand    |
| February | Does not show aggregated cpu frequency data     |
| Contains some information that does not show elsewhere    |Does not show aggregated cpu cache data    |
|     |Hard to understand how many cores per cpu especially if hyperthreading is enabled    |
|      | Some sections there lack proper description or verbose description to the items listed in them    |
|      | Lists a section per core and virtual core, so it's output is so long and repeated    |
|      |No NUMA info displayed |



### `lscpu`
| Pros    | Cons |
| -------- | ------- |
| Nice aggregated data  | Might not exist by default in some systems    |
| Nice output format | Not all info is displayed     |
| Numa information is displayed    |  NUMA info is displayed in brief, just nodes and cpus  |
|  Aggregated cpu cache info is displayed   |    |
| Displayes a nice summary of vulnerabilities in the cpu with explanation     |    |


### `dmidecode --type processor`
| Pros    | Cons |
| -------- | ------- |
| Nice aggregated data  | requires root privileges    |
| Nice output format | Very limited info is displayed     |
| Voltage value is displayed    | No NUMA info displayed   |
|  CPU Flags have nice description that can not be found in other tools    |    |
|  Displayes a nice characteristics section that displays summary of cpu capabilities    |    |

### `numactl --hardware`
| Pros    | Cons |
| -------- | ------- |
| Nice repesntation for NUMA info including disatances and memory information  | Does not exsit by default, a 3rd party package must be installed    |
|  | Does not include any other cpu info     |

### `numastat`
| Pros    | Cons |
| -------- | ------- |
|Displays Numa statistics like hits & misses  | Does not exsit by default, package must be installed, a 3rd party package must be installed     |
|     | Does not include any other cpu info |
