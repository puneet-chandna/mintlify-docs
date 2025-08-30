CloudSim-HO-Research-V2 Detailed Documentation
1. Introduction
Welcome to the CloudSim HO Research V2 project! 🔱

This research framework is a specialized simulation environment built on CloudSim Plus to analyze and evaluate the performance of the Hippopotamus Optimization (HO) algorithm for Virtual Machine (VM) placement in cloud data centers.

The project is designed for research-grade experiments, offering a robust platform for comparing the HO algorithm against baseline allocation strategies like FirstFit, BestFit, and Genetic Algorithm (GA).

1.1. Key Objectives
Primary Objective: To provide a comprehensive implementation of the Hippopotamus Optimization algorithm for VM placement.

Secondary Objective: To statistically validate and compare the performance of the HO algorithm against other baseline algorithms.

Tertiary Objective: To conduct in-depth parameter sensitivity analysis and scalability testing to understand the algorithm's behavior under various conditions.

1.2. Core Metrics for Evaluation
The framework is designed to measure and analyze the following key performance indicators:

Resource Utilization: CPU and RAM usage efficiency.

SLA Violations: The number of times the service level agreement is breached.

Power Consumption: The energy efficiency of the data center.

Convergence: The speed and stability of the optimization algorithm.

2. Project Structure
The project follows a standard Maven project structure, organized into logical packages for clarity and maintainability.

Directory structure:
└── puneet-chandna-cloudsim-ho-research-v2/

    ├── LICENSE
    ├── pom.xml
    ├── run-experiment.ps1
    ├── run-experiment.sh
    ├── run-quick-test.ps1
    ├── run-quick-test.sh
    ├── run-simulation.ps1
    ├── run-simulation.sh
    
    ├── results/
    │   
    └── src/
        ├── main/
        │   ├── java/
        │   │   └── org/
        │   │       └── puneet/
        │   │           └── cloudsimplus/
        │   │               └── hiippo/
        │   │                   ├── App.java
        │   │                   ├── algorithm/
        │   │                   │   ├── AlgorithmConstants.java
        │   │                   │   ├── ConvergenceAnalyzer.java
        │   │                   │   ├── Hippopotamus.java
        │   │                   │   ├── HippopotamusOptimization.java
        │   │                   │   └── HippopotamusParameters.java
        │   │                   ├── baseline/
        │   │                   │   ├── BestFitAllocation.java
        │   │                   │   ├── FirstFitAllocation.java
        │   │                   │   └── GeneticAlgorithmAllocation.java
        │   │                   ├── exceptions/
        │   │                   │   ├── HippopotamusOptimizationException.java
        │   │                   │   ├── ScalabilityTestException.java
        │   │                   │   ├── StatisticalValidationException.java
        │   │                   │   └── ValidationException.java
        │   │                   ├── policy/
        │   │                   │   ├── AllocationValidator.java
        │   │                   │   ├── BaselineVmAllocationPolicy.java
        │   │                   │   └── HippopotamusVmAllocationPolicy.java
        │   │                   ├── simulation/
        │   │                   │   ├── CloudSimHOSimulation.java
        │   │                   │   ├── DatacenterFactory.java
        │   │                   │   ├── ExperimentCoordinator.java
        │   │                   │   ├── HODatacenterBroker.java
        │   │                   │   ├── QuickTest.java
        │   │                   │   ├── ScalabilityTester.java
        │   │                   │   ├── ScenarioGenerator.java
        │   │                   │   └── TestScenarios.java
        │   │                   ├── statistical/
        │   │                   │   ├── ANOVAResult.java
        │   │                   │   ├── ComparisonAnalyzer.java
        │   │                   │   ├── ConfidenceInterval.java
        │   │                   │   └── StatisticalValidator.java
        │   │                   └── util/
        │   │                       ├── BatchProcessor.java
        │   │                       ├── CSVResultsWriter.java
        │   │                       ├── ExperimentConfig.java
        │   │                       ├── MemoryManager.java
        │   │                       ├── MetricsCollector.java
        │   │                       ├── PerformanceMonitor.java
        │   │                       ├── ProgressTracker.java
        │   │                       ├── ResultValidator.java
        │   │                       ├── RunManager.java
        │   │                       ├── ScenarioConfigLoader.java
        │   │                       └── ValidationUtils.java
        │   └── resources/
        │       ├── algorithm_parameters.properties
        │       ├── config.properties
        │       └── logback.xml
        └── test/
            └── java/
                └── org/
                    └── puneet/
                        └── cloudsimplus/
                            └── hiippo/
                                ├── AppTest.java
                                └── unit/
                                    ├── BatchProcessorTest.java
                                    ├── ExperimentConfigTest.java
                                    ├── HippopotamusOptimizationExceptionTest.java
                                    ├── HippopotamusOptimizationTest.java
                                    ├── MemoryManagerTest.java
                                    ├── ProgressTrackerTest.java
                                    ├── ScalabilityTestExceptionTest.java
                                    ├── StatisticalValidationExceptionTest.java
                                    └── ValidationExceptionTest.java


2.1. Key Directories
Directory	Description
src/main/java	Contains the core Java source code for the simulation framework.
src/main/resources	Includes configuration files like config.properties and logback.xml.
src/test/java	Contains all the unit and integration tests for the project.
results/	The default directory for storing all the simulation results and logs.
target/	Maven's build directory, containing the compiled code and packaged JAR files.

3. Getting Started
3.1. Prerequisites
Java Development Kit (JDK) 21: The project is built using Java 21.

Maven 3.9+: Required for building the project and managing dependencies.

3.2. Building the Project
To build the project, run the following command from the root directory:

Bash

mvn clean install 
This will compile the source code and download all the required dependencies.

3.3. Running the Simulation
You can run the complete experimental suite using the run-experiment.ps1 for windows and run-experiment.sh for linux. or use the run-simulation.ps1 and run-simulation.sh for windows and linux respectively.


================================================
FILE: pom.xml
================================================
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    
    <groupId>org.puneet.cloudsimplus.hiippo</groupId>
    <artifactId>cloudsim-ho-research-v2</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    
    <properties>
        <maven.compiler.source>21</maven.compiler.source>
        <maven.compiler.target>21</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <cloudsimplus.version>8.5.7</cloudsimplus.version>
        <commons.math3.version>3.6.1</commons.math3.version>
        <commons.csv.version>1.10.0</commons.csv.version>
        <logback.version>1.4.14</logback.version>
        <junit.version>5.10.1</junit.version>
    </properties>
    
    <dependencies>
        <!-- CloudSim Plus -->
        <dependency>
            <groupId>org.cloudsimplus</groupId>
            <artifactId>cloudsimplus</artifactId>
            <version>${cloudsimplus.version}</version>
        </dependency>
        
        <!-- Apache Commons Math (Statistical Analysis) -->
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-math3</artifactId>
            <version>${commons.math3.version}</version>
        </dependency>
        
        <!-- Apache Commons CSV -->
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-csv</artifactId>
            <version>${commons.csv.version}</version>
        </dependency>
        
        <!-- SLF4J API -->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
            <version>2.0.7</version>
        </dependency>
        
        <!-- Logback Core -->
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-core</artifactId>
            <version>${logback.version}</version>
        </dependency>
        
        <!-- Logback Classic -->
        <dependency>
            <groupId>ch.qos.logback</groupId>
            <artifactId>logback-classic</artifactId>
            <version>${logback.version}</version>
        </dependency>
        
        <!-- Janino - Required for Logback conditional expressions -->
        <dependency>
            <groupId>org.codehaus.janino</groupId>
            <artifactId>janino</artifactId>
            <version>3.1.10</version>
        </dependency>
        
        <!-- JUnit Testing -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <version>${junit.version}</version>
            <scope>test</scope>
        </dependency>
        
        <!-- AssertJ for Advanced Testing -->
        <dependency>
            <groupId>org.assertj</groupId>
            <artifactId>assertj-core</artifactId>
            <version>3.25.3</version>
            <scope>test</scope>
        </dependency>
        </dependencies>
    

    
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.11.0</version>
                <configuration>
                    <source>21</source>
                    <target>21</target>
                    <compilerArgs>
                        <arg>-parameters</arg>
                    </compilerArgs>
                </configuration>
            </plugin>
            
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.0.0-M7</version>
                <configuration>
                    <argLine>-Xmx4G -Xms2G</argLine>
                    <parallel>methods</parallel>
                    <threadCount>2</threadCount>
                </configuration>
            </plugin>
            
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>exec-maven-plugin</artifactId>
                <version>3.1.0</version>
                <configuration>
                    <mainClass>org.puneet.cloudsimplus.hiippo.App</mainClass>
                    <commandlineArgs>-Xmx45G -Xms45G -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -Xloggc:gc.log -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./heapdump.hprof -XX:+DisableExplicitGC</commandlineArgs>
                </configuration>
            </plugin>
            
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-shade-plugin</artifactId>
                <version>3.4.1</version>
                <executions>
                    <execution>
                        <phase>package</phase>
                        <goals>
                            <goal>shade</goal>
                        </goals>
                        <configuration>
                            <transformers>
                                <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                    <mainClass>org.puneet.cloudsimplus.hiippo.App</mainClass>
                                </transformer>
                                <transformer implementation="org.apache.maven.plugins.shade.resource.ServicesResourceTransformer"/>
                                <transformer implementation="org.apache.maven.plugins.shade.resource.ApacheLicenseResourceTransformer"/>
                                <transformer implementation="org.apache.maven.plugins.shade.resource.ApacheNoticeResourceTransformer"/>
                            </transformers>
                            <filters>
                                <filter>
                                    <artifact>*:*</artifact>
                                    <excludes>
                                        <exclude>META-INF/*.SF</exclude>
                                        <exclude>META-INF/*.DSA</exclude>
                                        <exclude>META-INF/*.RSA</exclude>
                                        <exclude>module-info.class</exclude>
                                        <exclude>META-INF/versions/*/module-info.class</exclude>
                                    </excludes>
                                </filter>
                            </filters>
                            <minimizeJar>false</minimizeJar>
                            <shadedArtifactAttached>false</shadedArtifactAttached>
                            <createDependencyReducedPom>false</createDependencyReducedPom>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
        
        <!-- Resources configuration goes inside build -->
        <resources>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
            </resource>
        </resources>
    </build>
</project>


================================================
FILE: run-experiment.ps1
================================================
Param(
    [switch]$SkipTests
)

Write-Host "=========================================="
Write-Host "CloudSim HO Research Experiment Runner"
Write-Host "=========================================="
Write-Host "Heap Configuration: 50GB (initial and max)"
Write-Host "System: Windows PowerShell"
Write-Host ("Date: {0}" -f (Get-Date))
Write-Host "=========================================="

# Ensure Maven is available
if (-not (Get-Command mvn -ErrorAction SilentlyContinue)) {
    Write-Error "Maven is not installed or not in PATH. Install Maven and reopen PowerShell."
    exit 1
}

# Check total physical memory in GB
try {
    $cs = Get-CimInstance -ClassName Win32_ComputerSystem
    $totalMemGB = [math]::Round($cs.TotalPhysicalMemory / 1GB)
} catch {
    Write-Warning "Unable to determine system memory. Proceeding without memory check."
    $totalMemGB = $null
}

if ($null -ne $totalMemGB) {
    Write-Host "Total system memory: $totalMemGB GB"
    if ($totalMemGB -lt 64) {
        Write-Warning "System has less than 64GB RAM. 50GB heap may cause issues."
    }
}

# Build the project (compile only)
Write-Host "Building project..."
$compileArgs = @('clean','compile','-q')
if ($SkipTests) { $compileArgs += '-DskipTests' }
mvn @compileArgs
if ($LASTEXITCODE -ne 0) {
    Write-Error "Build failed"
    exit $LASTEXITCODE
}
Write-Host "Build successful!"

# Run the experiment via Maven exec plugin
Write-Host "Starting experiment..."
$execArgs = @('exec:java','-q','-Dexec.mainClass=org.puneet.cloudsimplus.hiippo.App')
mvn @execArgs
if ($LASTEXITCODE -eq 0) {
    Write-Host ""
    Write-Host "=========================================="
    Write-Host "Experiment completed successfully!"
    Write-Host "Results saved in: results/"
    Write-Host "Check logs for detailed information."
    Write-Host "=========================================="
} else {
    Write-Host ""
    Write-Host "=========================================="
    Write-Error "Experiment failed! Check logs for error details."
    Write-Host "=========================================="
    exit $LASTEXITCODE
}


================================================
FILE: run-experiment.sh
================================================
#!/bin/bash

# CloudSim HO Research Experiment Runner
# Updated for 8GB heap configuration
# author: Puneet Chandna
# date: 2025-08-01
# version: 1.0.0
# description: This script runs the CloudSim HO Research Experiment.
# It is used to run the experiment with the 8GB heap configuration.

echo "=========================================="
echo "CloudSim HO Research Experiment Runner"
echo "=========================================="
echo "Heap Configuration: 50GB (initial and max)"
echo "System Memory: 64GB"
echo "Date: $(date)"
echo "=========================================="

# Check if Maven is available
if ! command -v mvn &> /dev/null; then
    echo "Error: Maven is not installed or not in PATH"
    exit 1
fi

# Check available memory
echo "Checking system memory..."
TOTAL_MEM=$(free -g | awk '/^Mem:/{print $2}')
echo "Total system memory: ${TOTAL_MEM}GB"

if [ "$TOTAL_MEM" -lt 64 ]; then
    echo "Warning: System has less than 64GB RAM. 50GB heap may cause issues."
    read -p "Continue anyway? (y/N): " -n 1 -r
    echo
    if [[ ! $REPLY =~ ^[Yy]$ ]]; then
        exit 1
    fi
fi

# Clean and build the project
echo "Building project..."
mvn clean compile -q
if [ $? -ne 0 ]; then
    echo "Error: Build failed"
    exit 1
fi

echo "Build successful!"

# Run the experiment
echo "Starting experiment with 50GB heap configuration..."
echo "This may take 1-2 hours for the complete experimental suite."
echo ""

# Run with Maven exec plugin (uses pom.xml configuration)
mvn exec:java -Dexec.mainClass="org.puneet.cloudsimplus.hiippo.App" -q

# Check exit status
if [ $? -eq 0 ]; then
    echo ""
    echo "=========================================="
    echo "Experiment completed successfully!"
    echo "Results saved in: results/"
    echo "Check logs for detailed information."
    echo "=========================================="
else
    echo ""
    echo "=========================================="
    echo "Experiment failed!"
    echo "Check logs for error details."
    echo "=========================================="
    exit 1
fi 


================================================
FILE: run-quick-test.ps1
================================================
# Quick Test Script for CloudSim HO Research (PowerShell)
# This script runs a minimal experiment to verify performance improvements
# Optimized for 64GB RAM system

Write-Host "==========================================" -ForegroundColor Green
Write-Host "CloudSim HO Research - Quick Performance Test" -ForegroundColor Green
Write-Host "64GB System Optimized Configuration" -ForegroundColor Cyan
Write-Host "==========================================" -ForegroundColor Green

# Set Java options for better performance on 64GB system
$env:JAVA_OPTS = "-Xmx32g -Xms16g -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:+UseStringDeduplication"

Write-Host "Java Options: $env:JAVA_OPTS" -ForegroundColor Yellow
Write-Host "Starting quick performance test..." -ForegroundColor Yellow

# Run the main App (complete experimental suite)
Write-Host "Running complete experimental suite..." -ForegroundColor Yellow
# Build
mvn clean compile -q
if ($LASTEXITCODE -ne 0) { exit $LASTEXITCODE }

# Run
mvn exec:java -q -Dexec.mainClass=org.puneet.cloudsimplus.hiippo.App

Write-Host "Quick test completed!" -ForegroundColor Green
Write-Host "Check results/ directory for output files." -ForegroundColor Yellow



================================================
FILE: run-quick-test.sh
================================================
#!/bin/bash

# Quick Test Script for CloudSim HO Research
# This script runs a minimal experiment to verify performance improvements
# Optimized for 64GB RAM system

echo "=========================================="
echo "CloudSim HO Research - Quick Performance Test"
echo "64GB System Optimized Configuration"
echo "=========================================="

# Set Java options for better performance on 64GB system
export JAVA_OPTS="-Xmx32g -Xms16g -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:+UseStringDeduplication"

echo "Java Options: $JAVA_OPTS"
echo "Starting quick performance test..."

# Run the experiment with minimal configuration
mvn clean compile exec:java -Dexec.mainClass="org.puneet.cloudsimplus.hiippo.App" \
    -Dexec.args="--quick-test --scenarios=Micro,Small --replications=3" \
    -Djava.util.logging.config.file=src/main/resources/logback.xml

echo "Quick test completed!"
echo "Check results/ directory for output files." 


================================================
FILE: run-simulation.ps1
================================================
# CloudSim HO Research Experiment Runner
# Updated for JAR execution with heap configuration
# author: Puneet Chandna
# date: 2025-08-01
# version: 1.0.0
# description: This script runs the CloudSim HO Research Experiment using JAR files.
# It is used to run the experiment with the 50GB heap configuration.

Write-Host "=========================================="
Write-Host "CloudSim HO Research Experiment Runner"
Write-Host "=========================================="
Write-Host "Heap Configuration: 45GB (initial and max)"
Write-Host "System Memory: 64GB"
Write-Host "Date: $(Get-Date)"
Write-Host "=========================================="

# Check available memory
Write-Host "Checking system memory..."
$TOTAL_MEM = [math]::Round((Get-WmiObject -Class Win32_OperatingSystem).TotalVisibleMemorySize / 1MB, 2)
Write-Host "Total system memory: ${TOTAL_MEM}GB"

if ($TOTAL_MEM -lt 64) {
    Write-Host "Warning: System has less than 64GB RAM. 45GB heap may cause issues."
    $continue = Read-Host "Continue anyway? (y/N)"
    if ($continue -ne 'y' -and $continue -ne 'Y') {
        Exit
    }
}

# Check if the JAR file exists
$JAR_PATH = "target/cloudsim-ho-research-experiment.jar"
if (-Not (Test-Path $JAR_PATH)) {
    Write-Host "Error: JAR file not found at $JAR_PATH"
    Exit
}

# Java heap and GC flags
$JAVA_FLAGS = "-Xms45G -Xmx45G -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -Xloggc:gc.log -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./heapdump.hprof -XX:+DisableExplicitGC"

# Run the experiment with the configured JAR
Write-Host "Starting experiment with 45GB heap configuration..."
Write-Host "This may take 1-2 hours for the complete experimental suite."
Write-Host ""

# Execute JAR file with the configured heap and GC settings
java $JAVA_FLAGS -jar $JAR_PATH

# Check exit status
if ($LASTEXITCODE -eq 0) {
    Write-Host ""
    Write-Host "=========================================="
    Write-Host "Experiment completed successfully!"
    Write-Host "Results saved in: results/"
    Write-Host "Check logs for detailed information."
    Write-Host "=========================================="
} else {
    Write-Host ""
    Write-Host "=========================================="
    Write-Host "Experiment failed!"
    Write-Host "Check logs for error details."
    Write-Host "=========================================="
    Exit
}



================================================
FILE: run-simulation.sh
================================================
#!/bin/bash

# CloudSim HO Research Experiment Runner
# Updated for JAR execution with heap configuration
# author: Puneet Chandna
# date: 2025-08-01
# version: 1.0.0
# description: This script runs the CloudSim HO Research Experiment using JAR files.
# It is used to run the experiment with the 50GB heap configuration.

echo "=========================================="
echo "CloudSim HO Research Experiment Runner"
echo "=========================================="
echo "Heap Configuration: 45GB (initial and max)"
echo "System Memory: 64GB"
echo "Date: $(date)"
echo "=========================================="

# Check available memory
echo "Checking system memory..."
TOTAL_MEM=$(free -g | awk '/^Mem:/{print $2}')
echo "Total system memory: ${TOTAL_MEM}GB"

if [ "$TOTAL_MEM" -lt 64 ]; then
    echo "Warning: System has less than 64GB RAM. 45GB heap may cause issues."
    read -p "Continue anyway? (y/N): " -n 1 -r
    echo
    if [[ ! $REPLY =~ ^[Yy]$ ]]; then
        exit 1
    fi
fi

# Check if the JAR file exists
JAR_PATH="target/cloudsim-ho-research-experiment.jar"
if [ ! -f "$JAR_PATH" ]; then
    echo "Error: JAR file not found at $JAR_PATH"
    exit 1
fi

# Java heap and GC flags
JAVA_FLAGS="-Xms45G -Xmx45G -XX:+UseG1GC -XX:MaxGCPauseMillis=200 -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -Xloggc:gc.log -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./heapdump.hprof -XX:+DisableExplicitGC"

# Run the experiment with the configured JAR
echo "Starting experiment with 45GB heap configuration..."
echo "This may take 1-2 hours for the complete experimental suite."
echo ""

# Execute JAR file with the configured heap and GC settings
java $JAVA_FLAGS -jar "$JAR_PATH"

# Check exit status
if [ $? -eq 0 ]; then
    echo ""
    echo "=========================================="
    echo "Experiment completed successfully!"
    echo "Results saved in: results/"
    echo "Check logs for detailed information."
    echo "=========================================="
else
    echo ""
    echo "=========================================="
    echo "Experiment failed!"
    echo "Check logs for error details."
    echo "=========================================="
    exit 1
fi

4. The Hippopotamus Optimization (HO) Algorithm
The core of this research framework is the Hippopotamus Optimization (HO) algorithm, a nature-inspired metaheuristic algorithm that models the social behavior of hippos to solve complex optimization problems.

4.1. Core Concepts
Population: A set of "hippos," where each hippo represents a potential solution to the VM placement problem.

Fitness: A multi-objective function that evaluates the quality of each solution based on resource utilization, power consumption, and SLA violations.

Position Update: The process by which hippos move in the search space, influenced by the "leader" (the best solution) and "prey" (random solutions).

4.2. Implementation Details
The HO algorithm is implemented in the org.puneet.cloudsimplus.hiippo.algorithm package, with the following key classes:

HippopotamusOptimization.java: The main class that orchestrates the optimization process.

Hippopotamus.java: Represents a single solution (a hippo) in the population.

HippopotamusParameters.java: Encapsulates all the tunable parameters for the HO algorithm.

5. Simulation Workflow
The simulation is coordinated by the ExperimentCoordinator.java class, which manages the entire experimental workflow.

5.1. The Workflow Steps
Configuration: The coordinator loads the experimental setup from config.properties, including the scenarios and algorithms to be tested.

Scenario Generation: For each scenario, the TestScenarios.java class creates a set of VMs and hosts with specific configurations.

Experiment Execution: The ExperimentRunner.java class runs the simulation for each algorithm and scenario, for a specified number of replications.

Metrics Collection: During the simulation, the MetricsCollector.java class gathers all the relevant performance data.

Results Writing: The CSVResultsWriter.java class writes all the collected data to CSV files in the results/ directory.

Statistical Analysis: Finally, the ComparisonAnalyzer.java class performs statistical tests to compare the performance of the different algorithms.

6. Configuration
The framework is highly configurable, with all the key parameters managed through property files in the src/main/resources directory.

6.1. config.properties
This file controls the overall experimental setup:

Property	Description
experiment.replications	The number of times each experiment is repeated for statistical validity.
scenarios.enabled	A comma-separated list of scenarios to run (e.g., Micro, Small, Medium).
memory.max.heap.gb	The maximum heap size for the Java Virtual Machine (JVM).

Export to Sheets
6.2. algorithm_parameters.properties
This file contains the specific parameters for the HO and baseline algorithms:

Property	Description
ho.population.size	The number of hippos (solutions) in the population.
ho.max.iterations	The maximum number of generations the algorithm will run for.
ga.mutation.rate	The mutation rate for the Genetic Algorithm.

Export to Sheets
6.3. logback.xml
This file configures the logging framework, allowing you to control the level of detail and the output format of the logs. It includes strict size limits and log rotation policies to prevent excessive disk usage.

7. Results and Analysis
All the results from the simulation are saved in the results/ directory, organized by run ID. Each run includes raw data, statistical analysis, and logs.

7.1. Key Output Files
main_results.csv: Contains the raw, per-replication results for all experiments.

comparison_data/: Includes files for pairwise comparisons, algorithm rankings, and performance summaries.

statistical_analysis/: Contains the results of statistical tests, such as ANOVA and t-tests.

8. Testing
The project includes a comprehensive test suite to ensure the correctness and reliability of the framework.

8.1. Unit Tests
Unit tests are located in src/test/java/org/puneet/cloudsimplus/hiippo/unit and cover individual components of the framework.

8.2. Running Tests
To run all the tests, use the following Maven command:

Bash

mvn test