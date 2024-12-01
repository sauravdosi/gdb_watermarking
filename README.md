# Graph Database Watermarking with Pseudo-Nodes

## Overview

This project implements a novel watermarking technique for graph databases, embedding ownership indicators within the graph structure using pseudo-nodes. The method ensures data integrity and provenance without compromising database performance. It is resilient to ownership attacks and provides an efficient way of verifying data authenticity through watermark extraction.

The system utilizes Neo4j for graph database management and is implemented in Python 3.12. The process involves creating a fake graph that mimics the original, and using a private key to match embedded pseudo-nodes, proving the authenticity of the data.

## Features

- **Pseudo-Node Watermarking**: Embeds ownership markers into the graph structure using pseudo-nodes, maintaining operational integrity.
- **Attack Resilience**: Protects against ownership attacks such as guessing and deletion attacks.
- **Efficient Watermark Extraction**: Verifies data ownership by matching pseudo-nodes with a private key, without compromising performance.
- **Graph Database Verification**: Uses Neo4j as the graph database for storing and querying data.

## Requirements

- Python 3.12 or higher
- Neo4j
- Libraries:
  - `py2neo`
  - `pandas`
  - `hashlib`

## Installation

### Clone the repository

```bash
git clone https://github.com/yourusername/graph-watermarking.git
cd graph-watermarking
```

## Install dependencies
```bash
pip install -r requirements.txt
```

## Set up Neo4j

1. **Download and Install Neo4j**  
   - Download Neo4j from its [official website](https://neo4j.com/download/).  
   - Follow the installation instructions for your operating system.  

2. **Install Plugins**  
   - Install the APOC plugin for advanced procedures.  
   - Enable the plugin by adding the following lines to the `neo4j.conf` file:  
     ```plaintext
     dbms.security.procedures.unrestricted=apoc.*
     dbms.security.procedures.allowlist=apoc.*
     ```

3. **Set Up the Database**  
   - Start the Neo4j database server.  
   - Access the Neo4j browser at `http://localhost:7474`.  
   - Set up the database credentials (default username: `neo4j`). Update the password as prompted.  

4. **Using Py2neo for Queries**  
   - Install Py2neo using the following command:  
     ```bash
     pip install py2neo
     ```
   - Update the connection details in your Python scripts to match your Neo4j database credentials.  
   - Example connection code:  
     ```python
     from py2neo import Graph
     graph = Graph("neo4j://localhost:7687", auth=("<Your Username>", "<Your Password>"))

     ```


## Usage
Watermark Insertion
To insert a watermark into your graph database, run the following:

```bash
python insert_watermark.py --graph <your_graph>
```
This command inserts ownership markers into the graph, embedding pseudo-nodes to securely watermark the data.

## Watermark Extraction
To extract and verify the watermark, use the following command:

```bash
python extract_watermark.py --graph <your_graph> --private_key <your_private_key>
This process verifies the data's authenticity by matching the embedded pseudo-nodes using a private key.
```

## Attack Simulation
To simulate guessing and deletion attacks on the graph and assess the resilience of the watermark, run:

```bash
python simulate_attacks.py --graph <your_graph>
This will simulate various attack scenarios to verify the strength of the watermarking technique.
```

## Example Data:
To test with example graph data, you can load the provided sample dataset:

```bash
python load_sample_graph.py
```

This script will populate the database with a sample graph for experimentation and testing.

## Algorithm Description
Pseudo-Node List: A list of pseudo-nodes is maintained to verify the original database.
Watermark Insertion: A portion of the graph is embedded with ownership information using pseudo-nodes.
Watermark Extraction: A fake database is generated, and using a private key, the system searches for matching pseudo-nodes. A match confirms the watermark and proves data authenticity.
Contributions
- Original Paper: Graph Database Watermarking with Pseudo-Nodes
- Neo4j Documentation: Neo4j Docs
- Cryptography Tools: PyCryptodome
- Graph Database Resources: Graph Databases: Principles and Practice 
