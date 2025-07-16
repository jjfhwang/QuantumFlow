# QuantumFlow: Streamlining Quantum Circuit Optimization

QuantumFlow is a TypeScript library designed to facilitate the efficient optimization of quantum circuits. This library provides a suite of tools for representing, manipulating, and simplifying quantum circuits, enabling researchers and developers to accelerate the design and execution of quantum algorithms on various quantum computing platforms.

The core objective of QuantumFlow is to abstract away the complexities associated with quantum circuit representation and optimization. It achieves this through a modular architecture that allows users to define circuits using a high-level, intuitive API, subsequently leveraging built-in optimization routines to minimize gate counts and circuit depth. This leads to improved performance on noisy intermediate-scale quantum (NISQ) devices, where circuit fidelity is paramount. The library supports various common quantum gate sets and allows for the extension with custom gate definitions, providing a flexible environment for experimentation and algorithm development.

QuantumFlow offers significant benefits to quantum computing practitioners. First, it reduces the time and effort required to manually optimize quantum circuits, freeing up valuable resources for higher-level algorithm design. Second, it provides a standardized framework for quantum circuit representation, fostering collaboration and code reusability within the quantum computing community. Finally, it promotes the development of more efficient and robust quantum algorithms, paving the way for solving complex problems that are intractable for classical computers. QuantumFlow is positioned to be a valuable asset in the rapidly evolving landscape of quantum software development.

This library offers a crucial stepping stone towards the creation of more sophisticated quantum software, enabling developers to focus on higher-level algorithmic design without being bogged down in the complexities of low-level circuit manipulation. With its intuitive API and robust optimization routines, QuantumFlow aims to democratize quantum computing, making it more accessible and efficient for researchers, developers, and students alike.

## Key Features

*   **Quantum Circuit Representation:** Provides a robust and flexible class structure for representing quantum circuits. This includes methods for adding qubits, gates, and measurements. The internal representation utilizes sparse matrices for efficient storage and manipulation of quantum states.

*   **Gate Set Support:** Supports a variety of standard quantum gate sets, including Hadamard (H), Pauli-X (X), Pauli-Y (Y), Pauli-Z (Z), CNOT (CX), and controlled-Z (CZ) gates. Custom gate definitions can be added through the `addGate()` function, allowing for flexibility and extensibility. The `addGate()` function requires a name, the number of qubits the gate acts on, and a unitary matrix representing the gates operation.

*   **Circuit Optimization:** Implements various circuit optimization techniques, such as gate cancellation, gate merging, and Pauli simplification. These techniques aim to reduce the number of gates and the circuit depth, leading to improved performance on quantum hardware. The optimization algorithms leverage knowledge of gate identities and commutation relations.

*   **Quantum State Simulation:** Includes a quantum state simulator that allows users to verify the functionality of their circuits before deploying them to quantum hardware. The simulator uses a sparse vector representation of the quantum state, enabling efficient simulation of circuits with a moderate number of qubits. The simulation can be performed step-by-step, allowing for debugging and visualization of the quantum state evolution.

*   **Circuit Visualization:** Offers functionalities for visualizing quantum circuits in a human-readable format. This helps in understanding the circuit structure and identifying potential optimization opportunities. The visualization output can be customized to display different gate sets and circuit layouts.

*   **Platform Abstraction:** Provides a layer of abstraction between the quantum circuit representation and the underlying quantum hardware. This allows users to target different quantum computing platforms without modifying their circuit code. Future versions will include specific transpilers for IBM Quantum, Rigetti, and other platforms.

*   **Error Mitigation Strategies (Planned):** Future versions will incorporate error mitigation techniques to improve the reliability of quantum computations on noisy hardware. This includes methods such as zero-noise extrapolation and probabilistic error cancellation.

## Technology Stack

*   **TypeScript:** The primary programming language, chosen for its static typing, code maintainability, and scalability. TypeScript provides type safety and allows for better tooling and code completion compared to plain JavaScript.

*   **Node.js:** Used as the runtime environment for executing TypeScript code. Node.js provides a cross-platform environment for running the QuantumFlow library.

*   **npm (Node Package Manager):** Used for managing project dependencies and distributing the library. npm simplifies the process of installing and updating external libraries required by QuantumFlow.

*   **Linear Algebra Libraries (e.g., Math.js, numeric.js):** Chosen for efficient numerical computations, specifically matrix operations, which are fundamental to quantum circuit simulation and optimization. These libraries are optimized for performance and provide a wide range of mathematical functions.

*   **Jest (Testing Framework):** Used for writing and executing unit tests to ensure the correctness and reliability of the library. Jest provides a simple and efficient way to test TypeScript code.

## Installation

1.  **Prerequisites:** Ensure that Node.js and npm are installed on your system. You can download them from the official Node.js website.

2.  **Clone the repository:**

    git clone https://github.com/jjfhwang/QuantumFlow.git
    cd QuantumFlow

3.  **Install dependencies:**

    npm install

4.  **Build the project:**

    npm run build

## Configuration

QuantumFlow utilizes environment variables for configuring certain aspects of its behavior. Create a `.env` file in the project root directory and define the following variables as needed:

*   `LOG_LEVEL`: Specifies the logging level (e.g., `DEBUG`, `INFO`, `WARN`, `ERROR`). The default is `INFO`.
*   `SIMULATOR_MAX_QUBITS`: Sets the maximum number of qubits that the quantum state simulator can handle. The default is `10`. Increasing this value will increase memory consumption.
*   `OPTIMIZATION_LEVEL`: Sets the optimization level (0 for no optimization, 1 for basic optimization, 2 for advanced optimization). The default is `1`.

You will need to restart the application for the changes to take effect. Note that the .env file is not committed to the repository; it should be kept secret.

## Usage

Here's a basic example of how to use QuantumFlow to create and simulate a quantum circuit:

// Import the necessary modules
import { QuantumCircuit } from './src/QuantumCircuit';
import { HGate, CXGate, Measure } from './src/gates';

// Create a quantum circuit with 2 qubits
const circuit = new QuantumCircuit(2);

// Add a Hadamard gate to the first qubit
circuit.addGate(new HGate(0));

// Add a CNOT gate with the first qubit as control and the second as target
circuit.addGate(new CXGate(0, 1));

// Measure both qubits
circuit.addGate(new Measure(0));
circuit.addGate(new Measure(1));

// Simulate the circuit
const result = circuit.simulate();

// Print the measurement result
console.log(result);

API Documentation:

*   `QuantumCircuit(numQubits: number)`: Constructor for creating a quantum circuit with the specified number of qubits.
*   `addGate(gate: QuantumGate)`: Adds a gate to the circuit. QuantumGate is an abstract class, and specific gates (e.g. HGate, CXGate) must extend it.
*   `simulate(): number[]`: Simulates the circuit and returns the measurement results as an array of numbers.
*   `optimize(level: number)`: Optimizes the quantum circuit based on the specified optimization level (0, 1, or 2).
*   `toQASM(): string`: Returns the circuit in the OpenQASM format.

## Contributing

We welcome contributions to QuantumFlow! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise code with appropriate comments.
4.  Add unit tests to verify the correctness of your changes.
5.  Submit a pull request with a detailed description of your changes.
6.  Adhere to the existing code style and formatting.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/QuantumFlow/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the open-source community for providing valuable resources and tools that have contributed to the development of QuantumFlow. Specifically, we would like to acknowledge the contributions of the developers of TypeScript, Node.js, and various linear algebra libraries.