# TPTP Knowledge Representation: Knower, Truth, and Belief

This repository contains a TPTP (Thousands of Problems for Theorem Provers) formulation exploring a simple model of knowledge and belief, involving a knower, truths, and propositions.

## Overview

The project aims to formalize basic concepts of knowledge representation using higher-order logic (THF) in the TPTP language. It demonstrates how knowledge can be inferred from belief and the truth of a proposition.

## Current Formulation

The current TPTP file (`problem.tptp`) defines:

*   **Types:** `truth`, `knower`, `proposition`
*   **Constants:** `the_truth` (a specific truth), `the_knower` (a specific knower), `true_prop` (a specific proposition that is true under `the_truth`)
*   **Predicates:**
    *   `knows(knower, truth)`: Indicates whether a knower knows a truth.
    *   `holds(truth, proposition)`: Indicates whether a truth holds for a proposition (i.e., the proposition is true under that truth).
    *   `knows_prop(knower, proposition)`: Indicates whether a knower knows a proposition. *Note: Not used in axioms after introduction of `believes`.*
    *   `believes(knower, proposition)`: Indicates whether a knower believes a proposition.
*   **Axioms:**
    *   `truth_holds_for_true_prop`: `holds(the_truth, true_prop)` is true.
    *   `knower_believes_true_prop`: `believes(the_knower, true_prop)` is true.
    *   `belief_truth_to_knowledge`: If a knower believes a proposition, and a truth holds for that proposition, then the knower knows that truth. Formally: `![K: knower, P: proposition, T: truth]: ((believes(K, P) & holds(T, P)) => knows(K, T))`
* **Conjecture:**
	* `knows(the_knower, the_truth)`: The axioms logically entail that the knower knows the truth.  This is proven by showing that the knower believes a true proposition, and therefore knows the truth.

## Requirements

*   A TPTP-compatible theorem prover. The following have been tested:
    *   Leo-III (command-line interface)
    *   CVC5 (via SystemOnTPTP)
    *   Zipperpin (via SystemOnTPTP)
    *   SystemOnTPTP web interface: [http://systemontptp.com/](http://www.google.com/url?sa=E&source=gmail&q=http://systemontptp.com/)
*   Git (for version control - highly recommended)
*   GitHub Desktop (optional, for a graphical interface to Git)

## Usage

1.  **Clone the repository:**
     ```bash
     git clone <repository_url>
     ```
     (Replace `<repository_url>` with the URL of your GitHub repository.)

2.  **Run the prover:**

    *   **Using Leo-III (CLI):**
        ```bash
        java -jar leo3-v1.7.15.jar problem.tptp -t 300 -s -v 4
        ```
        (Adjust the path to `leo3-v1.7.15.jar` if necessary.  `-t 300` sets a timeout of 300 seconds. `-s` enables proof output, and `-v 4` sets the verbosity level.)

    *   **Using SystemOnTPTP:**
        1.  Go to [http://systemontptp.com/](http://www.google.com/url?sa=E&source=gmail&q=http://systemontptp.com/).
        2.  Select "Input Form".
        3.  Copy and paste the contents of `problem.tptp` into the input area.
        4.  Click "Submit".

3. **Expected output:** A successful run will report `SZS status Theorem`, indicating that the conjecture has been proven.

## Contributing

Contributions are welcome! Please follow these steps:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Make your changes.
4.  Commit your changes with clear commit messages.
5.  Create a pull request to merge your branch into `main`.

## Future Work

*   Extend the model to include justification, forming a complete JTB (justified true belief) account of knowledge.
*   Introduce multiple knowers and explore their interactions.
*   Model different levels of belief or confidence.
*   Investigate the use of model finders to explore different models of the axioms.
