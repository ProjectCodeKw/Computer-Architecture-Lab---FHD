# CpE-469 Lab Assignment #2: RISC-V Pipelined Datapath and Hazard Handling

## Objective

This assignment involved simulating and testing a RISC-V pipelined datapath, focusing on the forwarding and hazard detection unit developed previously. The core task was modifying this unit to handle additional forwarding and stall scenarios, particularly those involving the `ADDI` instruction. The goal was to gain a better understanding of how data hazards affect a pipelined processor and the importance of effective hazard handling for efficient execution.

## Tested Instructions & Hazards

A sequence of RISC-V instructions was used to test the modified pipeline, including `ADDI`, `ADD`, `BEQ`, `LW`, and `JAL`. Specific hazard types tested included:
* ADDI followed by a subsequent R-Type instruction.
* ADDI followed by a subsequent BEQ instruction.
* R-Type followed by a subsequent R-Type instruction.
* LW followed by a subsequent R-Type instruction (Load-Use hazard).
* JAL followed by a subsequent R-Type instruction.

## Implementation Details

* The architecture implemented limits forwarding paths, allowing only Memory stage and Write-Back stage to do forwarding. *(Self-correction based on prior conversation context: The final implementation discussed allowed MEM->ID, WB->MEM, WB->ID and MEM->EX forwarding)*.
* The Verilog code for the Forwarding and Hazard Detection unit (`FHD.v`) was modified, with the full code commented out to focus on running only the new modifications.

## Results Summary

* **Theoretical vs. Waveform:** The simulation results observed in the waveform (lab4.wvf) matched the expected theoretical outcomes, including register value changes and hazard occurrences.
* **Pipeline Execution:** The pipeline diagram showed the execution flow of 10 instructions, indicating detected data hazards and stalls. The JAL instruction correctly caused a jump, preventing the subsequent instruction (address 9) from being fully executed in the theoretical model, though it appears in the pipeline diagram as it enters the initial stages before the jump takes effect.
* **Debugging:** Outputs `ALUout` & `ALUoutM` were used for debugging and validation during simulation.

## Conclusion

The assignment successfully demonstrated the impact of data hazards in a pipelined RISC-V processor. Modifying the forwarding and hazard detection unit, specifically for `ADDI` instructions, improved execution efficiency. Testing with custom RISC-V code reinforced the importance of robust hazard handling for smooth pipeline operation. Further improvements are possible to enhance the processor's capabilities.

## Resources

* **Lab Manual:** Kuwait University, CpE-469 Computer Architecture Laboratory, Lab Manual.
* **Waveform File:** `lab4.wvf`.
* **Verilog Code:** `FHD.v` (modified version used).
